---
title: Spamtillidsniveau
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
ms.assetid: 34681000-0022-4b92-b38a-e32b3ed96bf6
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om det tillidsniveau til spam, der anvendes til meddelelser i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5a7bfd34fdb23b0bef94119f53adaa9ecc0c4a1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587538"
---
# <a name="spam-confidence-level-scl-in-eop"></a>SCL (Spam confidence level) i EOP

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser, bliver indgående meddelelser sendt via spamfiltrering i EOP og får tildelt en spamscore. Denne score er knyttet til et individuelt SCL-niveau (spam confidence level), som føjes til meddelelsen i et X-brevhoved. En højere SCL angiver, at en meddelelse er mere tilbøjelig til at være spam. EOP tager handling på meddelelsen baseret på SCL.

Hvad SCL betyder, og hvad standardhandlingerne, der er foretaget på meddelelser, er beskrevet i følgende tabel. Du kan finde flere oplysninger om handlinger, du kan udføre på meddelelser baseret på vurdering af spamfiltrering, under Konfigurer [politikker for uønsket post i EOP](configure-your-spam-filter-policies.md).

****

|SCL|Definition|Standardhandling|
|:---:|---|---|
|-1|Meddelelsen ignorerede spamfiltrering. Meddelelsen er f.eks. fra en afsender, der er tillid til, er blevet sendt til en modtager, der er tillid til, eller er fra en mailkildeserver på listen over tilladte IP-adresser. Få mere at vide under [Opret lister over afsendere, der er tillid til i EOP](create-safe-sender-lists-in-office-365.md).|Levering af meddelelsen til modtagernes indbakke.|
|0, 1|Spamfiltrering fandt, at meddelelsen ikke var spam.|Levering af meddelelsen til modtagernes indbakke.|
|5, 6|Spamfiltrering har markeret meddelelsen som **spam**|Levering af meddelelsen til modtagernes mappe med uønsket mail.|
|9|Spamfiltrering markerede meddelelsen som Spam **med høj fortrolighed**|Levering af meddelelsen til modtagernes mappe med uønsket mail.|
|

Du vil bemærke, at SCL 2, 3, 4, 7 og 8 ikke bruges til spamfiltrering.

Du kan bruge regler for mailflow (også kaldet transportregler) til at stemple SCL på meddelelser. Hvis du bruger en regel for mailflow til at angive SCL, udløser værdierne 5 eller 6 spamfiltreringshandlingen for **spam**, og værdierne 7, 8 eller 9 udløser spamfiltreringshandlingen **for Spam** med høj sikkerhed. Få mere at vide under [Brug regler for mailflow til at angive tillidsniveauet for spam i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Ligesom SCL identificerer masseforsendelsesniveauet (BCL) forkerte massemails (også kaldet _grå mail_). En højere BCL indikerer, at en massemailmeddelelse er mere tilbøjelig til at generere klager (og derfor er mere tilbøjelig til at være spam). Du skal konfigurere BCL-grænseværdien i antispampolitikker. Få mere at vide under Konfigurer [antispam-politikker i EOP](configure-your-spam-filter-policies.md), niveauet for masseklager [(BCL) i EOP)](bulk-complaint-level-values.md) og Hvad er forskellen på uønsket mail og massemails [?](what-s-the-difference-between-junk-email-and-bulk-email.md).

****

![Det korte ikon for LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Er du ny Microsoft 365?** Find gratis videokurser til **Microsoft 365 og it-fagfolk** gennem LinkedIn Learning.
