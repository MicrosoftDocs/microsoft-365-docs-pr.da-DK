---
title: Understøttelse af validering af domænenøgler identificerede mails (DKIM)
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
description: Få mere at vide om valideringen af DKIM-signerede meddelelser Exchange Online Protection og Exchange Online
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a5ea98add5ebe860f756d645909366a1f5502832
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588969"
---
# <a name="support-for-validation-of-dkim-signed-messages"></a>Understøttelse af validering af DKIM-signerede meddelelser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online Protection (EOP) og Exchange Online understøtter begge indgående validering af domænenøgler identificerede mails ([DKIM](https://www.rfc-editor.org/rfc/rfc6376.txt)).

DKIM validerer, at en mail ikke er blevet  efterlignet af en anden, og den er blevet sendt fra det domæne, *den hedder den* stammer fra. Den binder en mail til den organisation, der har sendt den. DKIM-bekræftelse bruges automatisk til alle meddelelser, der sendes med IPv6. Microsoft 365 understøtter også DKIM, når mail sendes via IPv4. (Du kan finde flere oplysninger om IPv6-understøttelse [i Support til anonyme indgående mails via IPv6](support-for-anonymous-inbound-email-messages-over-ipv6.md)).

DKIM validerer en digitalt signeret meddelelse, der vises DKIM-Signature brevhovedet i brevhovederne. Resultaterne af en DKIM-Signature er stemplet i sidehovedetAuthentication-Results brevhovedet. Teksten i brevhovedet ligner følgende (hvor contoso.com er afsenderen):

 `Authentication-Results: <contoso.com>; dkim=pass (signature was verified) header.d=example.com;`

> [!NOTE]
> Du kan finde flere oplysninger Authentication-Results brevhovedet i RFC 7001 (feltet Brevhoved til angivelse af [meddelelsesgodkendelsesstatus](https://www.rfc-editor.org/rfc/rfc7001.txt)). Microsofts DKIM-implementering er i overensstemmelse med denne RFC.

Administratorer kan oprette Exchange [regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) på resultaterne af DKIM-validering. Disse regler for mailflow giver administratorer mulighed for at filtrere eller distribuere meddelelser efter behov.