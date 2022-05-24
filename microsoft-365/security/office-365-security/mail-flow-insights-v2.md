---
title: Indsigt i mailflow i dashboardet Mailflow
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
description: Administratorer kan få mere at vide om den indsigt og de rapporter, der er tilgængelige på dashboardet Mailflow i Security & Compliance Center.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5850612fbd0de89e5eafe101f55d368b0f4b0c8f
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648717"
---
# <a name="mail-flow-insights-in-the-security--compliance-center"></a>Indsigt i mailflow i Security & Compliance Center

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Administratorer kan bruge dashboardet Mailflow i Security & Compliance Center til at finde tendenser, indsigt og udføre handlinger for at løse problemer, der er relateret til mailflow i deres organisation.

:::image type="content" source="../../media/mail-flow-dashboard-v2.png" alt-text="Dashboardet Mailflow i Security & Compliance Center" lightbox="../../media/mail-flow-dashboard-v2.png":::

De tilgængelige indsigter er:

- [Indsigt i automatisk videresendte meddelelser](mfi-auto-forwarded-messages-report.md)
- [Ret mulig indsigt i mailløkke1](mfi-mail-loop-insight.md)<sup></sup>
- [Ret indsigt i regler for langsomme mailflow1](mfi-slow-mail-flow-rules-insight.md)<sup></sup>
- [Oversigt over mailflow](mfi-mail-flow-map-report.md)
- [Nye domæner, der videresendes med mailindsigt2](mfi-new-domains-being-forwarded-email.md)<sup></sup>
- [Nye brugere videresender indsigt via mail2](mfi-new-users-forwarding-email.md)<sup></sup>
- [Ikke-accepteret domænerapport](mfi-non-accepted-domain-report.md)
- [Rapport om manglende levering](mfi-non-delivery-report.md)
- [Indsigt i udgående og indgående mailflow](mfi-outbound-and-inbound-mail-flow.md)
- [Indsigt i køer](mfi-queue-alerts-and-queues.md)
- [Indsigt og rapport om SMTP-godkendelsesklienter](mfi-smtp-auth-clients-report.md)
- [Indsigt i topdomænets status for mailflow](mfi-domain-mail-flow-status-insight.md)

<sup>1</sup> Denne indsigt vises først i området **Anbefalet for dig** på dashboardet Mailflow, når problemet er registreret. Ellers kan du ikke se den.

<sup>2</sup> Denne indsigt vises ikke på dashboardet Mailflow, men den er synlig på [siden Videresend rapport](view-mail-flow-reports.md#forwarding-report) , når problemet er registreret. Ellers kan du ikke se den.

## <a name="permissions-required-to-view-the-mail-flow-dashboard"></a>Tilladelser, der kræves for at få vist dashboardet Mailflow

Dashboardet Mailflow er tilgængeligt for medlemmer af følgende rollegrupper:

- **Organisationsadministration** i Security & Compliance Center (globale administratorer).

- **[Exchange administrator](/azure/active-directory/roles/permissions-reference#exchange-administrator)** i Azure Active Directory.

- **MailFlow-administrator** i Security & Compliance Center. Hvis kontoen ikke også er medlem af organisationsadministrationen eller Exchange administratorrollegrupper, skal du overveje følgende problemer:
  - Brugeren skal logge på Security & Compliance Center direkte på <https://protection.office.com>.
  - Brugeren har kun skrivebeskyttet tilladelse til dashboardet Mailflow.
  - Brugeren har ikke adgang til Microsoft 365 Administration.

Du kan få flere oplysninger om tilladelser [i Tilladelser i Security & Compliance Center](permissions-in-the-security-and-compliance-center.md) og [give brugerne adgang til Security & Compliance Center](grant-access-to-the-security-and-compliance-center.md).

## <a name="where-to-find-the-mail-flow-dashboard"></a>Her kan du finde dashboardet Mailflow

Hvis du vil gå direkte til dashboardet Mailflow, skal du åbne <https://protection.office.com/mailflow/dashboard>.
