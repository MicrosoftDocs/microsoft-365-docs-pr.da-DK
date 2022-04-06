---
title: Få vist mailflowrapporter i dashboardet Rapporter
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om de mailflowrapporter, der er tilgængelige i dashboardet Rapporter i & Compliance Center.
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d1fc133a8e05541f402e35cf8d62ee9662af661b
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476219"
---
# <a name="view-mail-flow-reports-in-the-reports-dashboard-in-security--compliance-center"></a>Få vist mailflowrapporter i dashboardet Rapporter i & Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> De fleste rapporter i denne artikel er også tilgængelige i Microsoft 365 Defender-portalen eller Exchange Administration (EAC). Du kan finde flere oplysninger i følgende emner:
>
> - [Mailflowrapporter i den nye Exchange Administration](/exchange/monitoring/mail-flow-reports/mail-flow-reports)
> - [Få vist mailsikkerhedsrapporter Microsoft 365 Defender portalen](view-email-security-reports.md)

Ud over de mailflowrapporter, der er tilgængelige i [dashboardet for mailflow](mail-flow-insights-v2.md) i Security & Compliance Center, findes der en række yderligere mailflowrapporter i dashboardet Rapporter, som kan hjælpe dig med at overvåge Microsoft 365 organisation.

Hvis du har de [nødvendige tilladelser](#what-permissions-are-needed-to-view-these-reports), kan du få vist disse rapporter i Security & Compliance Center ved at <https://protection.office.com> gå til **Dashboard for rapporter**\>. Hvis du vil gå direkte til dashboardet Rapporter, skal du åbne <https://protection.office.com/insightdashboard>.

:::image type="content" source="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png" alt-text="Dashboardet Rapporter i Security & Compliance Center" lightbox="../../media/6b213d34-adbb-44af-8549-be9a7e2db087.png":::

## <a name="connector-report"></a>Forbindelsesrapport

> [!NOTE]
> Denne rapport er blevet erstattet af rapporten **Indgående meddelelser og** rapporten **over udgående meddelelser** i EAC. Få mere at vide under [Indgående meddelelser og Udgående meddelelser-rapporter i den nye EAC](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports).

## <a name="exchange-transport-rule-report"></a>Exchange transportregelrapport

Rapporten **Exchange transportregel viser** effekten af regler for mailflow (også kaldet transportregler) på indgående og udgående meddelelser i organisationen.

For at få vist rapporten skal du åbne Security & Compliance Center på <https://protection.office.com>, gå til **Dashboard** **for rapporter** \> og **vælge Exchange Transportregel**. For at gå direkte til rapporten skal du åbne <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/scc-transport-rule-report-widget.png" alt-text="Widgetten Exchange transportregel i dashboardet Rapporter" lightbox="../../media/scc-transport-rule-report-widget.png":::

> [!NOTE]
> Rapporten **Exchange transportregel er** nu tilgængelig i EAC. Du kan finde flere oplysninger [Exchange rapport over transportregel i den nye EAC](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

## <a name="forwarding-report"></a>Rapport for videresendelse

> [!NOTE]
> Rapporten **til videresendelse** er nu tilgængelig i EAC. Du kan finde flere oplysninger [i Rapporten om automatisk videresendte meddelelser i det nye EAC](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Statusrapport for mailflow

**Statusrapporten Mailflow svarer** til rapporten Sendt og modtaget [mail med yderligere](#sent-and-received-email-report) oplysninger om mails, der er tilladt eller blokeret i kanten. Dette er den eneste rapport, der indeholder oplysninger om edge protection og viser, hvor meget mail der blokeres, før de bliver tilladt i tjenesten til evaluering af Exchange Online Protection (EOP). Det er vigtigt at forstå, at hvis en meddelelse sendes til fem modtagere, tæller vi den som fem forskellige meddelelser og ikke én meddelelse.

Du kan få vist rapporten ved at åbne [Security & Compliance Center](https://protection.office.com), gå til **Dashboard for rapporter** \> og vælge **Statusrapport for mailflow**. Hvis du vil gå direkte til **statusrapporten for mailflowet**, skal du åbne <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/scc-mail-flow-status-report-widget.png" alt-text="Widget'en Statusrapport for mailflow i dashboardet Rapporter" lightbox="../../media/scc-mail-flow-status-report-widget.png":::

> [!NOTE]
> Når du klikker på widgetten for denne rapport i Security & Compliance Center (protection.office.com), kommer du nu til den fulde rapport på Microsoft 365 Defender-portalen (security.microsoft.com). Hvis du vil have mere at vide om rapporten, [skal du se Statusrapport for mailflow](view-email-security-reports.md#mailflow-status-report).

## <a name="sent-and-received-email-report"></a>Rapport over sendte og modtagne mails

> [!NOTE]
> Denne rapport er blevet erstattet af [statusrapporten Mailflow](#mailflow-status-report).

## <a name="top-senders-and-recipients-report"></a>Rapport over de mest populære afsendere og modtagere

De **hyppigste** afsendere og modtagere viser de mest populære meddelelsesafsendere i organisationen samt de øverste modtagere af meddelelser, der blev registreret af EOP og Defender for Office 365-beskyttelsesfunktioner.

Hvis du vil have vist rapporten, skal du åbne Security & Compliance Center <https://protection.office.com>på ,  \> gå til **Dashboard** til rapporter og vælge **Øverste afsendere og modtagere**. Hvis du vil gå direkte til rapporten, skal du åbne en af følgende URL-adresser:

- Defender for Office 365:<https://protection.office.com/TopSenderRecipientsATP>
- EOP: <https://protection.office.com/TopSenderRecipients>

:::image type="content" source="../../media/scc-top-senders-and-recipients-widget.png" alt-text="Widgetten Bedste afsendere og modtagere i dashboardet Rapporter" lightbox="../../media/scc-top-senders-and-recipients-widget.png":::

> [!NOTE]
> Selvom når du klikker på widgetten for denne rapport i Security & Compliance Center, kommer du til en protection.office.com-side, men sideindholdet kommer fra Microsoft 365 Defender-portalen. Hvis du vil have mere at vide om rapporten, [skal du se Rapporten Bedste afsendere og modtagere](view-email-security-reports.md#top-senders-and-recipients-report).

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Hvilke tilladelser er nødvendige for at få vist disse rapporter?

For at få vist og bruge de rapporter, der er beskrevet i denne artikel, skal du være medlem af en af følgende rollegrupper i Security & Compliance Center:

- **Organisationsadministration**
- **Sikkerhedsadministrator**
- **Sikkerhedslæser**
- **Global læser**

Du kan finde flere [oplysninger i Tilladelser i sikkerheds- & Compliance Center](permissions-in-the-security-and-compliance-center.md).

> [!NOTE]
> Hvis du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i Security & _Compliance Center og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="related-topics"></a>Relaterede emner

[Intelligente rapporter og indsigt i Security & Compliance Center](reports-and-insights-in-security-and-compliance.md)

[Indsigt i mailflow i Security & Compliance Center](mail-flow-insights-v2.md)

[Få vist mailsikkerhedsrapporter i Security & Compliance Center](view-email-security-reports.md)

[Få vist rapporter for Microsoft Defender for Office 365](view-reports-for-mdo.md)
