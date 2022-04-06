---
title: Rapport om manglende levering i dashboardet for mailflow
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om, hvordan du bruger rapporten om manglende levering i dashboardet for mailflow i Security & Compliance Center til at overvåge de mest anvendte fejlkoder i rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om ikke-leveret post) fra afsendere i organisationen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bc408f6bb28b11e77c49755b888c44e0ea4d9f57
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473733"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Rapport om manglende levering i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Rapporten om manglende levering i [dashboardet](mail-flow-insights-v2.md) mailflow i [Security & Compliance Center](https://protection.office.com) viser de mest stødte fejlkoder i rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om **ikke-leveret** post) for brugere i organisationen. Denne rapport viser detaljerne for rapporter om manglende levering (NDR) så du kan foretage fejlfinding af problemer med levering af mail.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="Widgetten Rapport om manglende levering i dashboardet mailflow i & Compliance Center" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>Rapportvisning for rapporten om manglende levering

Når du klikker på **widgetten til rapport om manglende** levering, kommer du til **rapporten om manglende levering**.

Som standard vises aktiviteten for alle fejlkoder. Hvis du klikker **på Vis data for**, kan du vælge en bestemt fejlkode på rullelisten.

Hvis du peger på en bestemt farve (fejlkode) på en bestemt dag i diagrammet, får du vist det samlede antal meddelelser for fejlen.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="Rapportvisningen i rapporten om det ikke-accepterede domæne" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>Detaljetabelvisning for rapport om manglende levering

Hvis du klikker **på Vis detaljetabel** i en rapportvisning, vises følgende oplysninger:

- **Dato**
- **Rapportkode for manglende levering**
- **Antal**
- **Eksempelbeskeder**: Meddelelses-sms'erne fra et eksempel på de berørte meddelelser.

Hvis du klikker **på** Filtre i en detaljeret tabelvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Hvis du vil sende rapporten for et bestemt datointerval til en eller flere modtagere, skal du klikke på **Anmod om download**.

Når du markerer en række i tabellen, vises en pop op-meddelelse med følgende oplysninger:

- **Dato**
- **Rapportkode for manglende levering**: Du kan klikke på linket for at finde flere oplysninger om årsager og løsninger til den specifikke fejlkode.
- **Antal**
- **Eksempelmeddelelser**: Du kan klikke på **Vis eksempelmeddelelser for** at få vist [resultaterne af meddelelsessporing](message-trace-scc.md) for et eksempel på de påvirkede meddelelser.


:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="Pop op-dialogboksen Detaljer efter valg af en række i tabelvisningen Detaljer i rapporten om manglende levering" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>Relaterede emner

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
