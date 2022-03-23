---
title: Backscatter i EOP
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
description: I denne artikel kan du få mere at vide om Backscatter og Microsoft Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79a6dd1be6c33bdbfc3d87b834f231de7cd08a0c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589141"
---
# <a name="backscatter-in-eop"></a>Backscatter i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Backscatter er* rapporter om manglende levering (også kaldet rapporter om manglende levering eller meddelelser om ikke-leveret mail), som du modtager for meddelelser, du ikke har sendt. Backscatter skyldes spammere, der spoofing skriver Fra-adressen ( `5322.From` også kaldet P2-adressen) i deres meddelelser. Afsendere af uønsket mail vil ofte bruge rigtige mailadresser som Fra-adressen til at give deres meddelelser troværdighed. Når spam sendes til en ikke-eksisterende modtager, bliver destinationsmailserveren i bund og grund narret til at returnere den meddelelse, der ikke kan leveres, i en NDR til den forfalskede afsender i Fra-adressen.

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser gør EOP alt for at identificere og uovervåget slippe meddelelser fra kedelige kilder uden at generere en NDR. Men baseret på den store mængde mail, der sendes gennem tjenesten, er der altid mulighed for, at EOP utilsigtet sender backscatter.

Backscatterer.org vedligeholder en blokeringsliste (også kaldet en DNS-blokeringsliste eller DNSBL) for mailservere, der var ansvarlige for at sende backscatter, og EOP-servere vises muligvis på denne liste. Men vi forsøger ikke at fjerne dig selv fra blokeringslisten i Backscatterer.org, fordi (ved deres egen optagelse) deres liste ikke er en liste over spammere.

> [!TIP]
> Webstedet Backscatterer.org (<http://www.backscatterer.org/?target=usage>) anbefaler at bruge deres tjeneste i Pengeskab i stedet for Afvis, fordi store mailtjenester næsten altid sender nogle backscatter.
