---
title: Rapportering og meddelelsessporing
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: f40253f2-50a1-426e-9979-be74ba74cb61
ms.custom:
- seo-marvel-apr2020
description: I denne artikel får du mere at vide om rapporter og fejlfindingsværktøjer, der er tilgængelige for Microsoft Exchange Online Protection-administratorer (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 929fce14a9e128b724b4aa69d88e4a3062ed5640
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682411"
---
# <a name="reporting-and-message-trace-in-eop"></a>Rapporterings- og meddelelsessporing i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser tilbyder EOP mange forskellige rapporter, der kan hjælpe dig med at bestemme organisationens overordnede status og tilstand. Der er også værktøjer, der kan hjælpe dig med at foretage fejlfinding af bestemte hændelser (f.eks. en meddelelse ikke ankommer til modtagerne), og overvågningsrapporter, der kan hjælpe med overholdelse af krav.

## <a name="usage-reports"></a>Brugsrapporter

- **Microsoft 365 gruppeaktivitet**: Få vist oplysninger om antallet af Microsoft 365, der oprettes og bruges. Du kan finde flere [oplysninger Microsoft 365 Rapporter i Administration – Microsoft 365 grupper](../../admin/activity-reports/office-365-groups.md).
- **Mailaktivitet**: Få vist oplysninger om antallet af meddelelser, der er sendt, modtaget og læst i hele organisationen og af bestemte brugere. Du kan finde flere [oplysninger Microsoft 365 Rapporter i Administration – mailaktivitet](../../admin/activity-reports/email-activity.md).
- **Brug af mailapps**: Få vist oplysninger om de mailapps, der bruges. Dette omfatter det samlede antal forbindelser for hver app og de versioner af Outlook, der opretter forbindelse. Du kan finde flere [oplysninger Microsoft 365 Rapporter i Administration – Brug af mailapps](../../admin/activity-reports/email-apps-usage.md).
- **Postkassebrug**: Få vist oplysninger om anvendt lagerplads, kvoteforbrug, elementantal og seneste aktivitet (send- eller læseaktivitet) for postkasser. Du kan finde flere oplysninger [Microsoft 365 Rapporter i Administration – Postkassebrug](../../admin/activity-reports/mailbox-usage.md).

## <a name="security-reports-in-the-microsoft-365-defender-portal"></a>Sikkerhedsrapporter på Microsoft 365 Defender Portal

Disse forbedrede rapporter giver en interaktiv rapporteringsoplevelse for EOP-administratorer, som indeholder oversigtsoplysninger og mulighed for at analysere ned for at få flere oplysninger.

- **Defender til Office 365**: Få vist oplysninger om Pengeskab Links og Pengeskab Vedhæftede filer, der er en del af Microsoft Defender Office 365. Du kan finde flere oplysninger [i View Defender for Office 365-rapporter på Microsoft 365 Defender-portalen](view-reports-for-mdo.md).
- **EOP**: Få vist oplysninger om malwareregistreringer, falske mails, spamregistreringer og mailflow til og fra din organisation. Du kan få mere at vide [under Få vist mailsikkerhedsrapporter Microsoft 365 Defender portalen](view-email-security-reports.md).

## <a name="mail-flow-insights-in-the-security--compliance-center"></a>Indsigt i mailflow i Security & Compliance Center

Få mere at vide under [Indsigt i mailflow i Security & Compliance Center](mail-flow-insights-v2.md).

## <a name="custom-reports-using-microsoft-graph"></a>Brugerdefinerede rapporter ved hjælp af Microsoft Graph

Opret rapporter, der er tilgængelige i Administration, ved hjælp af Microsoft Graph. Få mere at vide under [Oversigt over Microsoft Graph](/graph/overview) [Og Arbejde med Office 365 brugsrapporter i Microsoft Graph](/graph/api/resources/report).

## <a name="message-trace"></a>Meddelelsessporing

Følger mails, mens de sendes gennem EOP. Du kan se, om en mail er blevet modtaget, afvist, udskudt eller leveret af tjenesten. Den viser også, hvilke handlinger der blev foretaget på meddelelsen, før den nåede dens endelige status.

Du kan bruge disse oplysninger til effektivt at besvare dine brugeres spørgsmål, foretage fejlfinding af problemer med mailflow, validere ændringer i politikker og afhjælper behovet for at kontakte teknisk support for at få hjælp.

Se [Meddelelsessporing i Microsoft 365 Defender portal](message-trace-scc.md).

## <a name="audit-logging"></a>Overvågningslogføring

Registrerer bestemte ændringer, der er foretaget af administratorer i din organisation. Disse rapporter kan hjælpe dig med at foretage fejlfinding af konfigurationsproblemer eller finde årsagen til problemer, der er relateret til sikkerhed eller overholdelse af regler og standarder. Se [Overvågningsrapporter i Exchange Online](/exchange/security-and-compliance/exchange-auditing-reports/exchange-auditing-reports).

## <a name="reporting-and-message-trace-data-availability-and-latency"></a>Tilgængelighed og ventetid for rapporterings- og meddelelsessporingsdata

I følgende tabel beskrives det, hvornår EOP-rapporterings- og meddelelsessporingsdata er tilgængelige og i hvor lang tid.

|Rapporttype|Tilgængelige data (efter udløbsperiode)|Ventetid|
|---|---|---|
|Oversigtsrapporter for mailbeskyttelse|90 dage|Sammenlægning af meddelelsesdata er for det meste fuldført inden for 24-48 timer. Nogle mindre trinvise aggregerede ændringer kan forekomme i op til 5 dage.|
|Detaljerede rapporter om mailbeskyttelse|90 dage|For detaljerede data, der er mindre end 7 dage gamle, bør data blive vist inden for 24 timer, men de er muligvis først fuldførte efter 48 timer. Nogle mindre trinvise ændringer kan forekomme i op til 5 dage. <p> Hvis du vil have vist detaljerede rapporter for meddelelser, der er mere end 7 dage gamle, kan det tage op til et par timer, før resultaterne vises.|
|Meddelelsessporingsdata|90 dage|Når du kører en meddelelsessporing for meddelelser, der er mindre end 7 dage gamle, bør meddelelserne blive vist inden for 5-30 minutter.<p> Når du kører en meddelelsessporing for meddelelser, der er mere end 7 dage gamle, kan det tage op til et par timer.|

> [!NOTE]
> Datatilgængelighed og ventetid er den samme, uanset om du bliver bedt om det via Administration eller Remote PowerShell.
