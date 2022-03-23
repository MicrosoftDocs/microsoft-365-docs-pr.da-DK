---
title: Tilføj understøttelse af anonym indgående mail via IPv6
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratoren kan lære, hvordan du konfigurerer understøttelse af anonym indgående mail fra IPv6-kilder Exchange Online og Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78b2e653aa284e34af2315ac696d7390dce71884
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63589565"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Tilføj understøttelse af anonym indgående mail over IPv6 Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 organisationer med Exchange Online-postkasser og enkeltstående Exchange Online Protection (EOP)-organisationer uden Exchange Online-postkasser understøtter anonym indgående mail via IPv6. IPv6-kildemailserveren skal opfylde begge følgende krav:

- IPv6-kildeadressen skal have en gyldig POST (reverse DNS lookup), der gør det muligt for destinationen at finde domænenavnet fra IPv6-adressen.

- Afsenderen skal bestå enten SPF-bekræftelse (defineret i [RFC 7208](https://tools.ietf.org/html/rfc7208)) eller [DKIM-godkendelse](http://dkim.org/) (defineret i [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Før din organisation kan modtage anonym indgående mail via IPv6, skal en administrator kontakte Microsoft Support og bede om det. Du kan finde instruktioner om, hvordan du åbner en supportanmodning, [under Kontakt support for virksomhedsprodukter – hjælp til administratorer](../../admin/get-help-support.md).

Når anonym indgående IPv6-meddelelsessupport er aktiveret i din organisation, gennemgår meddelelsen den normale filtrering af meddelelser, der leveres af tjenesten.

## <a name="troubleshooting"></a>Fejlfinding

- Hvis kildemailserveren ikke har en IPv6-omvendt DNS-opslagspost, afvises meddelelserne med følgende fejl:

  > 450 4.7.25-tjenesten er ikke tilgængelig og sender IPv6-adresse [2a01:111:f200:2004::240] skal have omvendt DNS-post.

- Hvis afsenderen ikke passerer SPF- eller DKIM-validering, afvises meddelelserne med følgende fejl:

  > 450 4.7.26 Tjenesten er ikke tilgængelig, meddelelse sendt via IPv6 [2a01:111:f200:2004::240] skal bestå enten SPF- eller DKIM-validering.

- Hvis du forsøger at modtage anonyme IPv6-meddelelser, før du har tilmeldt dig, afvises meddelelsen med følgende fejl:

  > 550 5.2.1 Tjenesten er ikke tilgængelig, [contoso.com] accepterer ikke mail via IPv6.

## <a name="related-topics"></a>Relaterede emner

[Understøttelse af validering af DKIM-signerede meddelelser](support-for-validation-of-dkim-signed-messages.md)
