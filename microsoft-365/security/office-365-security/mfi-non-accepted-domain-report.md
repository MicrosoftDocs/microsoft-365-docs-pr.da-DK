---
title: Ikke-accepteret domænerapport i dashboardet for mailflow
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
description: Administratorer kan se, hvordan de bruger rapporten over ikke-accepterede domæner i dashboardet for mailflow i Security & Compliance Center til at overvåge meddelelser fra din lokale organisation, hvor afsenderens domæne ikke er konfigureret i Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 25a8b1adb882aa83861e936d48534fc0a5f826e4
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679670"
---
# <a name="non-accepted-domain-report-in-the-security--compliance-center"></a>Rapport om ikke-accepteret domæne i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Rapporten **Ikke-accepteret** domæne i [dashboardet for mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) viser oplysninger om meddelelser fra din lokale mailorganisation, hvor afsenderens domæne ikke er konfigureret som et accepteret domæne i din Microsoft 365-organisation.

Microsoft 365 begrænser muligvis disse meddelelser, hvis vi har data, der beviser, at formålet med disse meddelelser er skadeligt. Det er derfor vigtigt, at du forstår, hvad der sker, og løser problemet.

![Widget for ikke-accepteret domæne i mailflowdashboardet i & Compliance Center.](../../media/mfi-non-accepted-domain-report-widget.png)

## <a name="report-view-for-the-non-accepted-domain-report"></a>Rapportvisning for rapporten om det ikke-accepterede domæne

Når du klikker på diagrammet på **widgetten Ikke-accepteret** domæne, kommer du til **rapporten over ikke-accepteret** domæne.

Som standard vises aktiviteten for alle berørte forbindelser. Hvis du klikker **på Vis data for**, kan du vælge en bestemt forbindelse på rullelisten.

Hvis du peger på et datapunkt (dag) i diagrammet, får du vist det samlede antal meddelelser for forbindelsen.

![Rapportvisning i rapporten om ikke-accepteret domæne.](../../media/mfi-non-accepted-domain-report-overview-view.png)

## <a name="details-table-view-for-the-non-accepted-domain-report"></a>Detaljetabelvisning for rapporten om det ikke-accepterede domæne

Hvis du klikker **på Vis detaljetabel** i en rapportvisning, vises følgende oplysninger:

- **Dato**
- **Navn på indgående forbindelse**
- **Afsenderdomæne**
- **Antal meddelelser**
- **Eksempelbeskeder**: Meddelelses-sms'erne fra et eksempel på de berørte meddelelser.

Hvis du klikker **på** Filtre i en detaljeret tabelvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Hvis du vil sende rapporten for et bestemt datointerval til en eller flere modtagere, skal du klikke på **Anmod om download**.

Når du markerer en række i tabellen, vises en pop op-meddelelse med følgende oplysninger:

- **Dato**
- **Navn på indgående forbindelse**
- **Afsenderdomæne**
- **Antal meddelelser**
- **Eksempelmeddelelser**: Du kan klikke på **Vis eksempelmeddelelser for** at få vist [resultaterne af meddelelsessporing](message-trace-scc.md) for et eksempel på de påvirkede meddelelser.

![Pop op-billede med detaljer efter valg af en række i tabelvisningen Detaljer i rapporten Ikke-accepteret domæne.](../../media/mfi-non-accepted-domain-report-details-flyout.png)

Klik på Vis rapport for at gå tilbage til **rapportvisningen**.

## <a name="related-topics"></a>Relaterede emner

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
