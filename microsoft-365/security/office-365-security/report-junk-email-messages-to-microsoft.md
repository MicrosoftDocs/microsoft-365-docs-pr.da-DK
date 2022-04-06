---
title: Rapportér spammeddelelser, ikke-spam- og phishingmeddelelser til Microsoft
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: c31406ea-2979-4fac-9288-f835269b9d2f
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om de forskellige måder at rapportere gode og dårlige meddelelser og filer til Microsoft til analyse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f7818b15d97d8d7ee33005927ff899e9f5ff5a06
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682719"
---
# <a name="report-messages-and-files-to-microsoft"></a>Rapportér meddelelser og filer til Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser har både brugere og administratorer flere forskellige metoder til rapportering af mails og filer til Microsoft.

|Metode|Beskrivelse|
|---|---|
|[Brug portalen til indsendelser til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft](admin-submission.md)|Den anbefalede rapporteringsmetode for administratorer i organisationer med Exchange Online (ikke tilgængelig i enkeltstående EOP).|
|[Aktivere rapportmeddelelsen eller phishing-tilføjelses ins](enable-the-report-message-add-in.md)|Fungerer med Outlook og Outlook på internettet (tidligere kaldet Outlook Web App). <p> Afhængigt af dit abonnement er meddelelser, som brugere rapporterede med tilføjelses ins[, tilgængelige](admin-submission.md) i portalen for administratorindsendelser, resultater af automatiseret undersøgelse og svar [(AIR](air-view-investigation-results.md)), rapporten om brugerrapporterede meddelelser og [Stifinder](threat-explorer-views.md#email--submissions).[](view-email-security-reports.md#user-reported-messages-report) <p> Du kan konfigurere rapporterede meddelelser til at blive kopieret eller omdirigeret til en postkasse, som du angiver. Få mere at vide under [Politikker for brugerindsendelse](user-submission.md).
|[Rapportér falske positive og falske negativer i Outlook](report-false-positives-and-false-negatives.md)|Indsend falske positive (god mail, der blev blokeret eller sendt til mappen Uønsket) og falske negativer (uønsket mail eller phish, der blev leveret til indbakken) til Exchange Online Protection (EOP) ved hjælp af funktionen Rapportmeddelelse.|
|[Brug regler for mailflow til at se, hvad brugerne rapporterer til Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft)|Få mere at vide om, hvordan du opretter en regel for mailflow (også kaldet en transportregel), der giver dig besked, når brugere rapporterer meddelelser til Microsoft til analyse.|
|[Send malware og ikke-malware til Microsoft til analyse](submitting-malware-and-non-malware-to-microsoft-for-analysis.md)|Brug webstedet Microsoft Sikkerhedsviden til at sende vedhæftede filer og andre filer.|

> [!NOTE]
> Data fra indsendelser til Microsoft befinder sig Office 365 grænse for overholdelse i nordamerikanske datacentre. Dataene gennemgås af analytikere på det tekniske team for at hjælpe med at forbedre effektiviteten af filtrene. Indsendelsen betragtes som feedback for at hjælpe med at forbedre filtrene og gemmes i en periode på 30 dage. Derefter slettes den.
