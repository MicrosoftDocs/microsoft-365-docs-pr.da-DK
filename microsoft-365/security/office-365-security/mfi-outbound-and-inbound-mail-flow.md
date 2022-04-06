---
title: Indsigt i udgående og indgående mailflow i dashboardet for mailflow
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
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: Administratorer kan få mere at vide om indsigt i udgående og indgående mailflow i dashboardet for mailflow i Security & Compliance Center.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3bc9d6c08dfc1c232018d79e988d741505079604
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475713"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Indsigt i udgående og indgående mailflow i & Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Indsigt i udgående og **indgående mailflow** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) kombinerer oplysningerne fra forbindelsesrapporten og den tidligere **TLS-oversigtsrapport** på ét sted.[](view-mail-flow-reports.md#connector-report)

Widgetten viser den TLS-kryptering, der bruges til forbindelsen, når meddelelser sendes til og fra din organisation. De forbindelser, der er oprettet med andre mailtjenester, krypteres af TLS, når TLS tilbydes af begge sider. Widgetten giver et øjebliksbillede af den seneste uges mailflow.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png" alt-text="Widgetten Udgående og indgående mailflow i dashboardet for mailflow i & Security & Compliance Center" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png":::

Oplysningerne i widgetten er relateret til forbindelser og TLS-meddelelsesbeskyttelse i Microsoft 365. Du kan finde flere oplysninger i disse emner:

- [Konfigurere mailflow ved hjælp af forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Sådan Exchange Online du bruger TLS til at sikre mailforbindelser](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [Tekniske referenceoplysninger om kryptering i Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>Meddelelse beskyttet under overførsel (af TLS)

Når du klikker **på Vis detaljer** på widgetten, viser pop op-pop-op-pop-op'en Meddelelse, der er beskyttet under overførsel **(af TLS),** dig TLS-beskyttelsen for meddelelser, der kommer ind i og forlader organisationen.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png" alt-text="Pop op-pop op'en Meddelelser beskyttet under overførsel (med TLS), der vises, når du klikker på Vis detaljer på widgetten Udgående og Indgående mail" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png":::

TLS 1.2 er i øjeblikket den mest sikre version af TLS, der tilbydes af Microsoft 365. Ofte skal du kende den TLS-kryptering, der bruges til overholdelsesrevisioner. Du har sandsynligvis ikke en direkte relation til de fleste kilde- og destinationsmailservere (du ejer ikke dem, og det har Microsoft heller ikke), så du ikke har mange muligheder for at forbedre TLS-kryptering, der bruges af disse servere.

Du kan dog bruge forbindelser [til](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) at sikre den bedste tilgængelige TLS-beskyttelse til meddelelser, der sendes mellem dine mailservere og Microsoft 365. Mailflow mellem Microsoft 365 og dine egne mailservere eller -servere, der tilhører dine partnere, er ofte vigtigere og mere følsomme end almindelige meddelelser, så det er en god ide at anvende ekstra sikkerhed og fleksibilitet til disse meddelelser.

Du kan opgradere eller rette dine egne mailservere for at forbedre den TLS-kryptering, der bruges, eller du kan kontakte dine partnere for at gøre det samme. **Forbindelsesrapporten viser** både mængden af mailflow og TLS-kryptering for meddelelser, der bruger Microsoft 365 forbindelsesforbindelser.

Du kan klikke på **linket forbindelsesrapport** for at gå til [forbindelsesrapporten](view-mail-flow-reports.md#connector-report). Følgende indsigter kan være tilgængelige på siden **Forbindelsesrapport** , hvis den tilknyttede betingelse er blevet registreret:

- **Indgående partnerforbindelse med et betydeligt TLS1.0-mailflow**
- **Indgående OnPremises-forbindelse med et betydeligt TLS1.0-mailflow**

For TLS 1.0-forbindelser er du nødt til at få din mailserver eller din partners server opgraderet eller rettet for at undgå problemer, når understøttelse af TLS 1.0 frarådes i Microsoft 365.

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).