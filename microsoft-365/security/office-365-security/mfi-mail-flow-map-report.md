---
title: Mailflowkort
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan lære, hvordan de bruger kortet Mailflow i dashboardet Mailflow i Security & Compliance Center til at visualisere og registrere, hvordan mailflows til og fra deres organisation over forbindelser og uden brug af forbindelser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 725489dc92fc43edab13c291129ed78c3ca7915e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588736"
---
# <a name="mail-flow-map-in-the-security--compliance-center"></a>Mailflowoversigt i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Mailflowoversigten** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) giver indsigt i, hvordan mail flyder gennem din organisation. Du kan bruge disse oplysninger til at lære mønstre, identificere anomalies og løse problemer, når de opstår.

![Widget for mailflowkort i dashboardet mailflow i & Compliance Center.](../../media/mfi-mail-flow-map-widget.png)

Widgetten viser som standard mønsteret for mailflow fra den forrige dag i et diagram kaldet et *Sankey-diagram* . Du kan bruge venstre pil ![Venstre pil.](../../media/scc-left-arrow.png) og højre pil ![Højre pil for](../../media/scc-right-arrow.png) at vise oplysninger fra forskellige dage. Hver forskellig farve repræsenterer mailflow over en forskellig indgående eller udgående forbindelse (eller uden brug af forbindelser). Hvis du peger på en bestemt farve, vises antallet af meddelelser for den pågældende type forbindelse.

## <a name="report-view-for-the-mail-flow-map"></a>Rapportvisning for mailflowoversigten

Når du klikker på **widgetten Mail-flowkort** , kommer du til **rapporten Mailflow Map** .

Følgende diagrammer er tilgængelige i rapportvisningen:

- **Vis data for: Oversigt**: Dette er grundlæggende en større visning af widgetten. Hvis du peger på en bestemt farve, vises antallet af meddelelser for den pågældende type forbindelse.

  ![Oversigtsvisning i rapporten Tilknyt mailflow.](../../media/mfi-mail-flow-map-report-overview.png)

- **Vis data for: Detaljer**: Denne visning viser detaljer om forbindelser og destinationsdomæner. De øverste afsender- og modtagerdomæner vises, og resten er angivet i **Andre**. Hvis du peger på en bestemt farve og sektion, vises antallet af meddelelser.

  ![Detaljevisning i rapporten Tilknyt mailflow.](../../media/mfi-mail-flow-map-report-detail.png)

Hvis du klikker **på** Filtre i en rapportvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Hvis du vil sende rapporten for et bestemt datointerval til en eller flere modtagere, skal du klikke på **Anmod om download**.

Relaterede indsigter vises under kortet Mailflow, hvis de er tilgængelige (f.eks. Fix [possible mail loop insight](mfi-mail-loop-insight.md).

## <a name="details-table-view-for-the-mail-flow-map"></a>Detaljetabelvisning for mailflowoversigten

Hvis du klikker **på Vis detaljetabel** i en rapportvisning, vises følgende oplysninger:

- **Dato**
- **Kategori**
- **Forbindelse/tredjeparts serviceudbyder**
- **Afsender/modtagerdomæne**
- **Antal meddelelser**

Hvis du klikker **på** Filtre i en detaljeret tabelvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Hvis du vælger en række, vises der lignende detaljer i en pop op-pop-op-uddeling:

![Pop op-meddelelse med detaljer fra detaljetabellen i oversigten over mailflow.](../../media/mfi-mail-flow-map-view-details-table-details.png)

Hvis du vil sende rapporten for et bestemt datointerval til en eller flere modtagere, skal du klikke på **Anmod om download**.

Klik på Vis rapport for at gå tilbage til **rapportvisningen**.

## <a name="see-also"></a>Se også

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
