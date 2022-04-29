---
title: Understøttelse af validering af domænenøgleidentificerede mails (DKIM)
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: a4c95148-a00c-4d12-85ed-88520b547d97
ms.collection:
- M365-security-compliance
description: Få mere at vide om validering af DKIM-signerede meddelelser i Exchange Online Protection og Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dcdd251ba1266033671ac524426d1ac3d2f56a10
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130708"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>Understøttelse af validering af DKIM-signerede meddelelser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) og Exchange Online begge understøtter indgående validering af [DKIM-meddelelser](https://www.rfc-editor.org/rfc/rfc6376.txt) (Domain Keys Identified Mail).

DKIM validerer, at en mail ikke blev *spoofed* af en anden, og blev sendt fra det domæne, den *siger* , den kom fra. Den knytter en mail til den organisation, der har sendt den. DKIM-bekræftelse bruges automatisk til alle meddelelser, der sendes med IPv6. Microsoft 365 understøtter også DKIM, når der sendes mail via IPv4. (Du kan få flere oplysninger om IPv6-understøttelse under [Understøttelse af anonyme indgående mails via IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md)).

DKIM validerer en digitalt signeret meddelelse, der vises i DKIM-Signature header i brevhovederne. Resultaterne af en DKIM-Signature validering stemples i Authentication-Results overskrift. Teksten i brevhovedet ser ud som følgende (hvor contoso.com er afsenderen):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Du kan få flere oplysninger om den Authentication-Results header i RFC 7001 ([Feltet Meddelelsesheader til angivelse af godkendelsesstatus for meddelelse](https://www.rfc-editor.org/rfc/rfc7001.txt). Microsofts DKIM-implementering er i overensstemmelse med denne RFC.

Administratorer kan oprette Exchange [regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) for resultaterne af DKIM-valideringen. Disse regler for mailflow giver administratorer mulighed for at filtrere eller distribuere meddelelser efter behov.
