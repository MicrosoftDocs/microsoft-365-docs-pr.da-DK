---
title: Backscatter i Exchange Online Protection
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
ms.assetid: 6f64f2de-d626-48ed-8084-03cc72301aa4
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: I denne artikel får du mere at vide om Backscatter og Microsoft Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d132ed56c02989987da9e0ce32e7d4593e85e651
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648211"
---
# <a name="backscatter-in-eop"></a>Backscatter i Exchange Online Protection

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Backscatter* er rapporter om manglende levering (også kendt som NDR'er eller meddelelser om manglende levering), som du modtager for meddelelser, du ikke sendte. Backscatter skyldes, at spammere forfalsker (spoofing) From-adressen (også kendt som `5322.From` P2-adressen) i deres meddelelser. Spammere vil ofte bruge rigtige e-mailadresser som Fra adresse til at låne troværdighed til deres meddelelser. Når spam sendes til en modtager, der ikke findes, er destinationsmailserveren i bund og grund narret til at returnere den meddelelse, der ikke kan leveres, i en NDR til den forfalskede afsender på Fra-adressen.

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection -organisationer (EOP) uden Exchange Online postkasser gør EOP alt for at identificere og uovervåget slippe meddelelser fra tvivlsomme kilder uden at generere en NDR. Men baseret på den store mængde e-mail, der flyder gennem tjenesten, er der altid mulighed for, at EOP utilsigtet sender backscatter.

Backscatterer.org vedligeholder en blocklist (også kendt som en DNS-blokeringsliste eller DNSBL) af mailservere, der var ansvarlige for at sende backscatter, og EOP-servere vises muligvis på denne liste. Men vi forsøger ikke at fjerne os fra Backscatterer.org blokliste, fordi (ved deres egen optagelse) deres liste er ikke en liste over spammere.

> [!TIP]
> Det Backscatterer.org websted (<http://www.backscatterer.org/?target=usage>) anbefaler at bruge deres tjeneste i Pengeskab tilstand i stedet for tilstanden Afvis, fordi store mailtjenester næsten altid sender nogle backscatter.
