---
title: Niveau for spamsikkerhed
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
description: Administratorer kan få mere at vide om det niveau for spamsikkerhed, der blev anvendt på meddelelser i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8febc1d0e0c4fd98b33fb0016beee89a30802241
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647903"
---
# <a name="spam-confidence-level-scl-in-eop"></a>Niveau for spamsikkerhed (SCL) i EOP

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser, går indgående meddelelser gennem spamfiltrering i EOP og tildeles en spamscore. Denne score er knyttet til et individuelt niveau for spamtillid (SCL), der føjes til meddelelsen i en X-header. En højere SCL angiver, at der er større sandsynlighed for, at en meddelelse er spam. EOP reagerer på meddelelsen baseret på SCL'en.

Hvad SCL betyder, og de standardhandlinger, der udføres på meddelelser, er beskrevet i følgende tabel. Du kan få flere oplysninger om de handlinger, du kan foretage på meddelelser, der er baseret på domsafsigelsen om spamfiltrering, [under Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md).

|SCL|Definition|Standardhandling|
|:---:|---|---|
|-1|Meddelelsen sprang over filtrering af spam. Meddelelsen er f.eks. fra en afsender, der er tillid til, blev sendt til en sikker modtager eller er fra en mailkildeserver på listen over tilladte IP-adresser. Du kan få flere oplysninger under [Opret lister over sikre afsendere i EOP](create-safe-sender-lists-in-office-365.md).|Send meddelelsen til modtagernes indbakke.|
|0, 1|Filtrering af spam bestemte, at meddelelsen ikke var spam.|Send meddelelsen til modtagernes indbakke.|
|5, 6|Filtrering af spam markerede meddelelsen som **spam**|Levér meddelelsen til modtagernes mappe med uønsket mail.|
|9|Filtrering af spam markerede meddelelsen som **spam med høj genkendelsessikkerhed**|Levér meddelelsen til modtagernes mappe med uønsket mail.|

Du vil bemærke, at SCL 2, 3, 4, 7 og 8 ikke bruges af spamfiltrering.

Du kan bruge regler for mailflow (også kaldet transportregler) til at stemple SCL'en på meddelelser. Hvis du bruger en regel for mailflow til at angive SCL'en, udløser værdierne 5 eller 6 filtreringshandlingen for **spam**, og værdierne 7, 8 eller 9 udløser spamfiltreringshandlingen for **spam med høj genkendelsessikkerhed**. Du kan få flere oplysninger under [Brug regler for mailflow til at angive niveauet for spamsikkerhed i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

Ligesom med SCL identificerer bulkklageniveauet (BCL) dårlig massemail (også kendt som _grå mail_). En højere BCL angiver, at der er større sandsynlighed for, at en massemailmeddelelse genererer klager (og er derfor mere tilbøjelige til at være spam). Du kan konfigurere grænsen for BCL i politikker til bekæmpelse af spam. Du kan få flere oplysninger under [Konfigurer politikker for uønsket mail i EOP](configure-your-spam-filter-policies.md), [BCL (Bulk complaint level) i EOP)](bulk-complaint-level-values.md) og [Hvad er forskellen mellem uønsket mail og massemail?](what-s-the-difference-between-junk-email-and-bulk-email.md)

****

![Det korte ikon for LinkedIn-Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Er du ny Microsoft 365?** Se gratis videokurser for **Microsoft 365 administratorer og it-teknikere**, som LinkedIn Learning har bragt til dig.
