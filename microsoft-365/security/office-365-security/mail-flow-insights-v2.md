---
title: Indsigt i mailflow i dashboardet for mailflow
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: beb6acaa-6016-4d54-ba7e-3d6d035e2b46
description: Administratorer kan få mere at vide om indsigter og rapporter, der er tilgængelige i dashboardet for mailflow i Security & Compliance Center.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b5cc3eba5807838b0a797f606d8a6aa3c152f60c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476461"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Indsigt i mailflow i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorer kan bruge dashboardet for mailflow i Security & Compliance Center til at opdage tendenser, indsigt og udføre handlinger for at løse problemer i forbindelse med mailflow i organisationen.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="Dashboardet Mailflow i sikkerheds- & Compliance Center" lightbox="../../media/mail-flow-dashboard-v2.png":::

De tilgængelige indsigter er:

- [Indsigt i automatisk videresendte meddelelser](mfi-auto-forwarded-messages-report.md)

- [Ret mulig indsigt i mailløkke1](mfi-mail-loop-insight.md)<sup></sup>

- [Ret regler for langsom mailflow1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>

- [Mailflowkort](mfi-mail-flow-map-report.md)

- [Nye domæner, der videresendes mail insight2](mfi-new-domains-being-forwarded-email.md)<sup></sup>

- [Nye brugere, der videresender mailindsigt2](mfi-new-users-forwarding-email.md)<sup></sup>

- [Rapport over ikke-accepteret domæne](mfi-non-accepted-domain-report.md)

- [Rapport om manglende levering](mfi-non-delivery-report.md)

- [Indsigt i udgående og indgående mailflow](mfi-outbound-and-inbound-mail-flow.md)

- [Indsigt i køer](mfi-queue-alerts-and-queues.md)

- [SMTP Auth-klienters indsigt og rapport](mfi-smtp-auth-clients-report.md)

- [Mest populære indsigt i mailflowstatus for domænet](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Dette indsigt vises først **i området** Anbefalet til dig i mailflowdashboardet, når problemet er registreret. Ellers kan du ikke se den.

<sup>2</sup> Dette indsigt vises ikke på dashboardet for mailflow, men er synlig på siden med rapporten [](view-mail-flow-reports.md#forwarding-report) om videresendelse, når problemet er registreret. Ellers kan du ikke se den.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Tilladelser, der kræves for at få vist mailflowdashboardet

Dashboardet Mailflow er tilgængeligt for medlemmer af følgende rollegrupper:

- **Organisationsadministration** i Security & Compliance Center (globale administratorer).

- **[Exchange administrator](/azure/active-directory/roles/permissions-reference#exchange-administrator)** i Azure Active Directory.

- **MailFlow-administrator** i Sikkerheds- & Compliance Center. Hvis kontoen ikke også er medlem af rollegrupperne Organisationsadministration Exchange administrator, skal du overveje følgende problemer:
  - Brugeren skal logge på Security & Compliance Center direkte på <https://protection.office.com>.
  - Brugeren har kun skrivebeskyttet tilladelse til dashboardet for mailflow.
  - Brugeren har ikke adgang til Microsoft 365 Administration.

Du kan finde flere oplysninger om tilladelser i Tilladelser i [Security & Compliance Center](permissions-in-the-security-and-compliance-center.md) og Give brugere adgang til [Security & Compliance Center](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Her finder du dashboardet for mailflow

Åbn Security & Compliance Center på <https://protection.office.com>, udvid **Mailflow**, og vælg derefter **Dashboard**.

For at gå direkte til mailflowdashboardet skal du åbne <https://protection.office.com/mailflow/dashboard>.