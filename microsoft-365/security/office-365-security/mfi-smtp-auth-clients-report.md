---
title: SMTP-klientindsigt og -rapport i dashboardet for mailflow
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
description: Administratorer kan lære, hvordan de bruger SMTP Auth-indsigt og -rapport i Mailflow-dashboardet i Security & Compliance Center til at overvåge mailafsendere i deres organisation, der bruger godkendt SMTP (SMTP AUTH) til at sende mails.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 30e3ff41068b80ad7c308fcb8163cb2748118e11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587321"
---
# <a name="smtp-auth-clients-insight-and-report-in-the-security--compliance-center"></a>SMTP Auth-klienters indsigt og rapport i Security & Compliance Center

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**SMTP-godkendt** klienters indsigt i [dashboardet til Mailflow](mail-flow-insights-v2.md) og den tilknyttede [SMTP-godkendt](#smtp-auth-clients-report) klientrapport i [Security & Compliance Center](https://protection.office.com) fremhæver brugeres eller systemkontis brug af SMTP AUTH-klientindsendelsesprotokol i organisationen. Denne ældre protokol (som bruger slutpunktsserveren smtp.office365.com) tilbyder kun grundlæggende godkendelse og er udsat for at blive brugt af kompromitterede konti til at sende mails. Med indsigt og rapporten kan du kontrollere for usædvanlig aktivitet for smtp auth-mailindsendelser. Den viser også TLS-forbrugsdata for klienter eller enheder, der bruger SMTP AUTH.

Widgetten angiver antallet af brugere eller tjenestekonti, der har brugt SMTP Auth-protokollen inden for de seneste 7 dage.

![Widgetten SMTP-klienter i dashboardet til mailflow i Security & Compliance Center.](../../media/mfi-smtp-auth-clients-report-widget.png)

Hvis du klikker på antallet af meddelelser på widgetten, vises en **pop op-vindue med SMTP-godkendelsesklikenter** . Pop-op-pop-op-uddelingen giver en samlet visning af TLS-brugen og -mængderne for den seneste uge.

![Pop op-menuen Detaljer, når du har klikket på widgetten SMTP Auth-klienter i mailflowdashboardet.](../../media/mfi-smtp-auth-clients-report-details.png)

Du kan klikke på linket **TIL SMTP-klienter** for at gå til rapporten over SMTP-auth-klienter som beskrevet i næste afsnit.

## <a name="smtp-auth-clients-report"></a>RAPPORT OVER SMTP-klienter

### <a name="report-view-for-the-smtp-auth-clients-report"></a>Rapportvisning for RAPPORTEN OVER SMTP-klienter

Rapporten viser som standard data for de seneste 7 dage, men der er tilgængelige data for de seneste 90 dage.

Sektionen Oversigt indeholder følgende diagrammer:

- **Vis data efter:** Afsendelse af mængde: Diagrammet viser som standard antallet af SMTP Auth-klientmeddelelser, der blev sendt fra alle domæner (Vis **data for:** Alle afsenderdomæner er valgt som standard). Du kan filtrere resultaterne til et bestemt afsenderdomæne ved at klikke på Vis **data for** og vælge afsenderdomænet på rullelisten. Hvis du peger på et bestemt datapunkt (dag), vises antallet af meddelelser.

  ![Afsendelse af volumenvisning i SMTP Auth-klienter-rapporten i Security & Compliance Center.](../../media/mfi-smtp-auth-clients-report-sending-volume-view.png)

- **Vis data efter: TLS-brug**: Diagrammet viser procentdelen af TLS-brugen for alle SMTP Auth-klientmeddelelser i den valgte tidsperiode. Dette diagram gør det muligt at identificere og handle på brugere og systemkonti, der stadig bruger ældre versioner af TLS.

  ![TLS-visning for brug i SMTP Auth-klienter i Security & Compliance Center.](../../media/mfi-smtp-auth-clients-report-tls-usage-view.png)

Hvis du klikker **på** Filtre i en rapportvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Klik **på Anmod** om rapport for at modtage en mere detaljeret version af rapporten i en mail. Du kan angive datointervallet og de modtagere, der skal modtage rapporten.

### <a name="details-table-view-for-the-smtp-auth-clients-report"></a>Detaljetabelvisning for rapport over SMTP-klienter

Hvis du klikker **på Vis detaljetabel**, afhænger de viste oplysninger af det diagram, du kigger på:

- **Vis data efter: Afsendelse af** lydstyrke: Følgende oplysninger er vist i en tabel:

  - **Afsenderadresse**
  - **Antal meddelelser**

  Hvis du markerer en række, vises de samme detaljer i en pop-op-pop-op-uddeling.

- **Få vist data efter: TLS-brug**: Følgende oplysninger er vist i en tabel:

  - **Afsenderadresse**
  - **TLS1,0 %**<sup>\*</sup>
  - **TLS1,1 %**<sup>\*</sup>
  - **TLS1,2 %**<sup>\*</sup>
  - **Antal meddelelser**

  <sup>\*</sup> Denne kolonne viser både procentdelen og antallet af meddelelser fra afsenderen.

Hvis du klikker **på** Filtre i en detaljeret tabelvisning, kan du angive et datointerval **med Startdato** **og Slutdato**.

Hvis du vælger en række, vises der lignende detaljer i en pop op-pop-op-uddeling:

![Pop op-billede med detaljer fra detaljetabellen i visningen TLS-brug i rapporten SMTP Auth-klienter.](../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png)

Klik **på Anmod** om rapport for at modtage en mere detaljeret version af rapporten i en mail. Du kan angive datointervallet og de modtagere, der skal modtage rapporten.

Klik på Vis rapport for at gå tilbage til **rapportvisningen**.

## <a name="related-topics"></a>Relaterede emner

Hvis du vil have mere at vide om andre indsigter i dashboardet for mailflow, skal du se Indsigt i [mailflow & Security & Compliance Center](mail-flow-insights-v2.md).
