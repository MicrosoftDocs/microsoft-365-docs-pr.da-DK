---
title: Rapport om manglende levering i dashboardet for mailflow
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
description: Administratorer kan få mere at vide om, hvordan du bruger rapporten om manglende levering i dashboardet for mailflow i Security & Compliance Center til at overvåge de mest anvendte fejlkoder i rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om ikke-leveret post) fra afsendere i organisationen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 00efa42dbe9f3ca119d407c74d3711d99d6c0d5c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589175"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Rapport om manglende levering i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Rapporten om manglende levering i [dashboardet](mail-flow-insights-v2.md) mailflow i [Security & Compliance Center](https://protection.office.com) viser de mest stødte fejlkoder i rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om **ikke-leveret** post) for brugere i organisationen. Denne rapport viser detaljerne for rapporter om manglende levering (NDR) så du kan foretage fejlfinding af problemer med levering af mail.

![Widget for rapport om manglende levering i dashboardet for mailflow i & Compliance Center.](../../media/mfi-non-delivery-report-widget.png)

## <a name="report-view-for-the-non-delivery-report"></a>Rapportvisning for rapporten om manglende levering

Når du klikker på **widgetten til rapport om manglende** levering, kommer du til **rapporten om manglende levering**.

Som standard vises aktiviteten for alle fejlkoder. Hvis du klikker **på Vis data for**, kan du vælge en bestemt fejlkode på rullelisten.

Hvis du peger på en bestemt farve (fejlkode) på en bestemt dag i diagrammet, får du vist det samlede antal meddelelser for fejlen.

![Rapportvisning i rapporten om ikke-accepteret domæne.](../../media/mfi-non-delivery-report-overview-view.png)

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

![Pop op-billede med detaljer efter markering af en række i tabelvisningen Detaljer i rapporten om manglende levering.](../../media/mfi-non-delivery-report-details-flyout.png)

## <a name="related-topics"></a>Relaterede emner

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
