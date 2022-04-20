---
title: Rapport, der ikke leveres, på dashboardet Mailflow
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
description: Administratorer kan få mere at vide om, hvordan de kan bruge rapporten med oplysninger om manglende levering på dashboardet Mailflow i Security & Compliance Center til at overvåge de oftest registrerede fejlkoder i rapporter om manglende levering (også kaldet NDR'er eller manglende meddelelser) fra afsendere i din organisation.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 663e145bcf9d6dc95f0f71b3b0b50a78419ed989
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64973503"
---
# <a name="non-delivery-report-in-the-security--compliance-center"></a>Rapport om manglende levering i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Rapporten Manglende levering** i [dashboardet Mailflow](mail-flow-insights-v2.md) i [Security & Compliance Center](https://protection.office.com) viser de mest registrerede fejlkoder i rapporter om manglende levering (også kendt som NDR'er eller meddelelser om manglende levering) for brugere i din organisation. Denne rapport viser detaljer om NDR'er, så du kan foretage fejlfinding af problemer med levering af mail.

:::image type="content" source="../../media/mfi-non-delivery-report-widget.png" alt-text="Rapportwidgetten Manglende levering på dashboardet Mailflow i Security & Compliance Center" lightbox="../../media/mfi-non-delivery-report-widget.png":::

## <a name="report-view-for-the-non-delivery-report"></a>Rapportvisning for rapporten om manglende levering

Hvis du klikker på **widgetten Rapport om manglende levering** , kommer du til **rapporten Om manglende levering**.

Som standard vises aktiviteten for alle fejlkoder. Hvis du klikker på **Vis data for**, kan du vælge en bestemt fejlkode på rullelisten.

Hvis du holder markøren over en bestemt farve (fejlkode) på en bestemt dag i diagrammet, får du vist det samlede antal meddelelser om fejlen.

:::image type="content" source="../../media/mfi-non-delivery-report-overview-view.png" alt-text="Visningen Rapport i den ikke-accepterede domænerapport" lightbox="../../media/mfi-non-delivery-report-overview-view.png":::

## <a name="details-table-view-for-the-non-delivery-report"></a>Detaljeret tabelvisning for rapporten om manglende levering

Hvis du klikker på **Vis detaljetabel** i en rapportvisning, vises følgende oplysninger:

- **Dato**
- **Rapportkode, der ikke leveres**
- **Tælle**
- **Eksempelmeddelelser**: Meddelelses-id'erne for et eksempel på berørte meddelelser.

Hvis du klikker på **Filtre** i en tabelvisning med detaljer, kan du angive et datointerval med **startdato** og **slutdato**.

Hvis du vil sende rapporten til et bestemt datointerval til en eller flere modtagere, skal du klikke på **Anmod om download**.

Når du markerer en række i tabellen, vises der et pop op-vindue med følgende oplysninger:

- **Dato**
- **Rapportkode, der ikke leveres**: Du kan klikke på linket for at finde flere oplysninger om årsager og løsninger til den specifikke fejlkode.
- **Tælle**
- **Eksempelmeddelelser**: Du kan klikke på **Vis eksempelmeddelelser** for at se [resultaterne af meddelelsessporingen](message-trace-scc.md) for et eksempel på de berørte meddelelser.

:::image type="content" source="../../media/mfi-non-delivery-report-details-flyout.png" alt-text="Pop op-vinduet Detaljer efter valg af en række i tabelvisningen Detaljer i rapporten Manglende levering" lightbox="../../media/mfi-non-delivery-report-details-flyout.png":::

## <a name="related-topics"></a>Relaterede emner

Du kan få oplysninger om anden indsigt i dashboardet Mailflow under [Mailflowindsigt i Security & Compliance Center](mail-flow-insights-v2.md).
