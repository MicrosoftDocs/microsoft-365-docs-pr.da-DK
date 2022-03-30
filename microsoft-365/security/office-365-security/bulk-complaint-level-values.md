---
title: Værdier for masseklageniveau
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a5b03b3c-37dd-429e-8e9b-2c1b25031794
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om værdier for masseannulleringsniveau (BCL), der bruges i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8c50ca25a355ca142e36c67d03fad42c3aa461a2
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679868"
---
# <a name="bulk-complaint-level-bcl-in-eop"></a>Masseklageniveau (BCL) i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser tildeler EOP en masse klageniveau (BCL) til indgående meddelelser fra massemailere. BCL føjes til meddelelsen i en X-brevhoved og svarer til det [tillidsniveau for spam,](spam-confidence-levels.md) der bruges til at identificere meddelelser som spam. En højere BCL indikerer, at massemeddelelsen er mere tilbøjelig til at generere klager (og derfor er mere tilbøjelig til at være spam). Microsoft bruger både interne kilder og tredjepartskilder til at identificere masseforsendelser og fastslå den relevante BCL.

Masseforsendelser varierer i deres afsendelsesmønstre, oprettelse af indhold og fremgangsmåder for anskaffelse af modtagere. Gode masseforsendelser sender ønskede meddelelser med relevant indhold til deres abonnenter. Disse meddelelser genererer få klager fra modtagere. Andre masseforsendelser sender uopfordrede meddelelser, der ligner spam, og som genererer mange klager fra modtagere. Meddelelser fra en masseforsendelse kaldes masseforsendelser eller grå mails.

 Spamfiltrering markerer meddelelser  som massemails baseret på BCL-grænsen (standardværdien eller en værdi, du angiver) og gør den angivne handling for meddelelsen (standardhandlingen er at levere meddelelsen til modtagerens mappe med Uønsket mail). Få mere at vide under [Konfigurer antispam-politikker](configure-your-spam-filter-policies.md) og [Hvad er forskellen på uønsket mail og massemail?](what-s-the-difference-between-junk-email-and-bulk-email.md)

BCL-tærskelværdierne er beskrevet i følgende tabel.

|BCL|Beskrivelse|
|:---:|---|
|0|Meddelelsen kommer ikke fra en masseafsender.|
|1, 2, 3|Meddelelsen kommer fra en masseafsender, der medfører færre klager.|
|4, 5, 6, 7<sup>\*</sup>|Meddelelsen kommer fra en masseafsender, der genererer et blandet antal klager.|
|8, 9|Meddelelsen kommer fra en masseafsender, som genererer et stort antal klager.|

<sup>\*</sup> Dette er standardtærskelværdien, der bruges i antispampolitikker.
