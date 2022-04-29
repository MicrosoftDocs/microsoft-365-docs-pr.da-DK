---
title: Indsigt i udgående og indgående mailflow på dashboardet Mailflow
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
description: Administratorer kan få mere at vide om indsigt i udgående og indgående mailflow i dashboardet Mailflow i Security & Compliance Center.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f856e2b9a4829531966802f2594f26c19e6ab7e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131190"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Indsigt i udgående og indgående mailflow i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Indsigten **for udgående og indgående mailflow** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) kombinerer oplysningerne fra [connectorrapporten](view-mail-flow-reports.md#connector-report) og den tidligere **TLS-oversigtsrapport** på ét sted.

Widgetten viser den TLS-kryptering, der bruges til forbindelsen, når meddelelser leveres til og fra din organisation. De forbindelser, der er etableret med andre mailtjenester, krypteres af TLS, når TLS tilbydes af begge sider. Widgetten tilbyder et snapshot af den sidste uges mailflow.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png" alt-text="Widgetten Udgående og indgående mailflow på dashboardet Mailflow i Security & Compliance Center" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png":::

Oplysningerne i widgetten er relateret til forbindelser og TLS-meddelelsesbeskyttelse i Microsoft 365. Du kan få flere oplysninger i disse emner:

- [Konfigurer mailflow ved hjælp af connectors](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Sådan bruger Exchange Online TLS til at sikre mailforbindelser](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [Tekniske referenceoplysninger om kryptering i Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>Meddelelse beskyttet under overførsel (af TLS)

Når du klikker på **Vis detaljer** på widgetten, viser pop op-vinduet **Meddelelse beskyttet under overførsel (af TLS)** TLS-beskyttelsen for meddelelser, der kommer ind i og forlader din organisation.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png" alt-text="Pop op-vinduet Meddelelser beskyttet under overførsel (af TLS), der vises, når du har klikket på Vis detaljer i widgetten Udgående og indgående mail" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png":::

I øjeblikket er TLS 1.2 den mest sikre version af TLS, der tilbydes af Microsoft 365. Du skal ofte kende den TLS-kryptering, der bruges til overvågning af overholdelse af angivne standarder. Du har sandsynligvis ikke en direkte relation til de fleste af kilde- og destinationsmailserverne (du ejer dem ikke, og det har Microsoft heller ikke), så du har ikke mange muligheder for at forbedre den TLS-kryptering, der bruges af disse servere.

Men du kan bruge [connectors](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) til at sikre den bedst tilgængelige TLS-beskyttelse for meddelelser, der sendes mellem dine mailservere og Microsoft 365. Mailflow mellem Microsoft 365 og dine egne mailservere eller servere, der tilhører dine partnere, er ofte vigtigere og mere følsomme end almindelige meddelelser, så du vil gerne anvende ekstra sikkerhed og årvågenhed på disse meddelelser.

Du kan opgradere eller løse dine egne mailservere for at forbedre den TLS-kryptering, der bruges, eller kontakte dine partnere for at gøre det samme. **Connectorrapporten** viser både diskenheden for mailflowet og TLS-kryptering for meddelelser, der bruger dine Microsoft 365 connectors.

Du kan klikke på linket **Connectorrapport** for at gå til [connectorrapporten](view-mail-flow-reports.md#connector-report). Følgende indsigter kan være tilgængelige på **rapportsiden Connector** , hvis den tilknyttede betingelse er blevet registreret:

- **Indgående partnerconnector ser et betydeligt TLS1.0-mailflow**
- **Connectoren Indgående onpremises ser et betydeligt TLS1.0-mailflow**

For TLS 1.0-forbindelser har du virkelig brug for at få din mailserver eller din partners server opgraderet eller løst for at undgå problemer, når understøttelse af TLS 1.0 til sidst frarådes i Microsoft 365.

## <a name="see-also"></a>Se også

Du kan få oplysninger om anden indsigt i dashboardet Mailflow under [Mailflowindsigt i Security & Compliance Center](mail-flow-insights-v2.md).
