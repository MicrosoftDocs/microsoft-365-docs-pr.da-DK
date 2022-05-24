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
description: Administration kan få mere at vide om, hvordan du konfigurerer understøttelse af anonyme indgående mails fra IPv6-kilder i Exchange Online og Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 093ab458e8894105536e1c3dd46d2c911de440fd
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649093"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Tilføj understøttelse af anonym indgående mail via IPv6 i Microsoft 365

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 organisationer med Exchange Online postkasser og enkeltstående Exchange Online Protection organisationer (EOP) uden Exchange Online postkasser understøtter anonyme indgående mails via IPv6. Kilde-IPv6-mailserveren skal opfylde begge følgende krav:

- IPv6-kildens adresse skal have en gyldig post med omvendt DNS-opslag (PTR), der gør det muligt for destinationen at finde domænenavnet fra IPv6-adressen.

- Afsenderen skal bestå enten SPF-bekræftelse (defineret i [RFC 7208](https://tools.ietf.org/html/rfc7208)) eller [DKIM-bekræftelse](http://dkim.org/) (defineret i [RFC 6376](https://www.rfc-editor.org/rfc/rfc6376.txt)).

Før din organisation kan modtage anonym indgående mail via IPv6, skal en administrator kontakte Microsoft Support og bede om det. Du kan finde oplysninger om, hvordan du åbner en supportanmodning, under [Kontakt support til forretningsprodukter – Administration Hjælp](../../admin/get-help-support.md).

Når anonym indgående IPv6-meddelelsesunderstøttelse er aktiveret i din organisation, gennemgår meddelelsen den normale meddelelsesfiltrering, der leveres af tjenesten.

## <a name="troubleshooting"></a>Fejlfinding

- Hvis kildemailserveren ikke har en omvendt DNS-opslagspost i IPv6, afvises meddelelserne med følgende fejl:

  > 450 4.7.25 Tjenesten er ikke tilgængelig, og IPv6-adressen [2a01:111:f200:2004::240] skal have omvendt DNS-post.

- Hvis afsenderen ikke består SPF- eller DKIM-valideringen, afvises meddelelserne med følgende fejl:

  > 450 4.7.26 Tjenesten er ikke tilgængelig, meddelelse sendt via IPv6 [2a01:111:f200:2004::240] skal bestå enten SPF- eller DKIM-validering.

- Hvis du forsøger at modtage anonyme IPv6-meddelelser, før du har tilmeldt dig, afvises meddelelsen med følgende fejl:

  > 550 5.2.1 Tjenesten er ikke tilgængelig, [contoso.com] accepterer ikke mail via IPv6.

## <a name="related-topics"></a>Relaterede emner

[Understøttelse af validering af DKIM-signerede meddelelser](support-for-validation-of-dkim-signed-messages.md)
