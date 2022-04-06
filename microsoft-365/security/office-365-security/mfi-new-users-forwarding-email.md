---
title: Nye brugere, der videresender mailindsigt
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.assetid: ''
description: Administratorer kan se, hvordan de kan bruge indsigt i videresendelse af mail i Security & Compliance Center til at undersøge, hvornår brugerne i organisationen videresender meddelelser til nye domæner.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 35ec1573096ecce392979cba11c6e55b1a1adcce
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681760"
---
# <a name="new-users-forwarding-email-insight-in-the-security--compliance-center"></a>Nye brugere, der videresender mailindsigt i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Det er mistænkeligt, når nye brugerkonti i organisationen pludselig begynder at videresende mails til eksterne domæner.

Det **nye domæne** , der videresender mailindsigt i [Security & Compliance Center](https://protection.office.com) , giver dig besked, når nyoprettede brugere i organisationen videresender meddelelser til eksterne domæner. Denne betingelse kunne angive, at kompromitterede administratorkonti blev brugt til at oprette de nye brugere. Hvis du har mistanke om, at kontiene er blevet kompromitteret, skal [du se Svare på en kompromitteret mailkonto](responding-to-a-compromised-email-account.md).

Dette indsigt vises kun, når problemet er registreret, og det vises på [rapportsiden for videresendelse](view-mail-flow-reports.md#forwarding-report) .

![Nye brugere videresender mailindsigt.](../../media/mfi-new-users-forwarding-email.png)

Når du klikker på widgetten, vises en pop op-meddelelse, hvor du kan finde flere oplysninger om de videresendte meddelelser, herunder [](#forwarding-modifications-report) et link til rapporten om videresendelse af ændringer som beskrevet senere i denne artikel.

![Pop op-vindue med detaljer, der vises, når du klikker på indsigt i mail, som nye brugere videresender.](../../media/mfi-new-users-forwarding-email-details.png)

Du kan også få adgang til denne detaljeside, når du vælger indsigten,  når du klikker på Vis alle i området **Top insights & anbefalinger** på (**Dashboard for** \> **rapporter eller ).** <https://protection.office.com/insightdashboard>

Du kan klikke på linket **Se rapport tilknyttet Insight** for at gå til **rapporten Videresendelse af ændringer** som beskrevet i næste afsnit.

## <a name="forwarding-modifications-report"></a>Rapport om videresendelse af ændringer

Rapporten **Videresendelse af ændringer** viser oplysninger om meddelelser, der automatisk videresendes fra afsendere i organisationen:

- Nyoprettede konti, der videresender meddelelser til eksterne domæner.
- Konti, der videresender meddelelser til eksterne domæner, som aldrig er blevet videresendt til af andre afsendere i organisationen.

Disse typer af videresendte meddelelser kan udgøre en sikkerhedsrisiko eller overensstemmelsesrisiko, og de kan angive kompromitterede konti.

Rapporten indeholder data for op til 90 dage. Rapporten viser som standard data for de seneste 7 dage.

Denne rapport er ikke direkte tilgængelig i dashboardet [til mailflow](mail-flow-insights-v2.md) eller i [dashboardet Rapporter](view-mail-flow-reports.md). Ud over at klikke på linket Se rapport tilknyttet **med indsigt** i indsigten  Nye brugere, der videresender mailindsigt, får du adgang til rapporten ved at:

- Når du klikker **på linket til videresendelse af** meddelelser i detaljerne om nye domæner [, der videresendes mailindsigt](mfi-new-domains-being-forwarded-email.md).
- Åbning <https://protection.office.com/reportv2?id=MailFlowNewForwarding>.

### <a name="report-view-for-the-forwarding-modifications-report"></a>Rapportvisning for rapporten Videresendelse af ændringer

Følgende diagrammer er tilgængelige i rapportvisningen:

- **Vis data for: Nye brugere af videresendelse**:

  ![Visningen Nye brugere til videresendelse i rapporten Videresendelse af ændringer.](../../media/forwarding-modifications-report-new-forwarding-users.png)

- **Vis data for: Nye videresendelsesdomæner**:

  ![Visningen Nye videresendte domæner i rapporten Videresendelse af ændringer.](../../media/forwarding-modifications-report-new-forwarded-domains.png)

Hvis du klikker **på** Filtre i en rapportvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

### <a name="details-table-view-for-the-forwarding-modifications-report"></a>Detaljetabelvisning for rapporten Videresendelse af ændringer

Hvis du klikker **på Vis detaljetabel**, afhænger de viste oplysninger af det diagram, du kigger på:

- **Vis data for: Nye brugere af videresendelse**:

  - **Navn**: Afsenderens mailadresse.
  - **Videresendelsestype**
  - **Modtageradresse**
  - **Detaljer**
  - **Antal**
  - **Første videresendelsesdato**

- **Vis data for: Nye videresendelsesdomæner**:

  - **Navn**: Afsenderens maildomæne.
  - **Videresendelsestype**
  - **Modtageradresse**
  - **Detaljer**
  - **Antal**
  - **Første videresendelsesdato**

Hvis du klikker **på** Filtre i en detaljeret tabelvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Hvis du vælger en række i tabellen, vises **pop op-dialogboksen** Detaljer med følgende oplysninger:

- **Navn**: Dette er enten afsenderens mailadresse (fra Visningen Vis **data for:** Visningen Nye brugere til videresendelse) eller afsenderens maildomæne (fra Vis **data for:** Visning af nye videresendelsesdomæner).
- **Videresendelsestype**
- **Modtager**
- **Detaljer**
- **Antal**
- **Startdato**
- **Anbefaling**: Herfra kan du klikke på linket for at administrere brugeren i Microsoft 365 Administration.

![Pop op-billede med detaljer i detaljetabellen i visningen Nye brugere til videresendelse i rapporten Videresendelse af ændringer.](../../media/mfi-forwarding-modifications-report-new-forwarding-users-view-details-table-details.png)

Klik på Vis rapport for at gå tilbage til **rapportvisningen**.

## <a name="related-topics"></a>Relaterede emner

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
