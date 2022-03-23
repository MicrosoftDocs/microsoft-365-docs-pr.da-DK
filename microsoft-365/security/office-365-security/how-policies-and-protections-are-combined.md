---
title: Rækkefølge og rangorden af mailbeskyttelse
keywords: sikkerhed, malware, Microsoft 365, M365, security center, Microsoft 365 Defender-portal, Microsoft Defender til slutpunkt, Microsoft Defender Office 365, Microsoft Defender til identitet
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om programrækkefølgen for beskyttelse i Exchange Online Protection (EOP), og hvordan prioritetsværdien i beskyttelsespolitikker bestemmer, hvilken politik der anvendes.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5fbccec656e0508535c2fbdaa055777a07968878
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588706"
---
# <a name="order-and-precedence-of-email-protection"></a>Rækkefølge og rangorden af mailbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser kan indgående mail blive markeret med flere former for beskyttelse. De indbyggede antiphishing-politikker i EOP, der er tilgængelige for alle Microsoft 365-kunder, og de mere robuste antiphishing-politikker, der er tilgængelige for Microsoft Defender for Office 365-kunder. Meddelelser passerer også gennem scanninger til flere registreringer for malware, spam, phishing osv. Under al denne aktivitet kan der være noget forvirring om, hvilken politik der anvendes.

Generelt er en politik, der anvendes på en meddelelse, identificeret i **X-Forefront Antispam-Report-overskriften** i **CAT (Kategori)** -egenskaben. Du kan få mere at vide [under Brevhoveder for uønsket post](anti-spam-message-headers.md).

Der er to overordnede faktorer, der bestemmer, hvilken politik der anvendes på en meddelelse:

- **Prioriteten af mailbeskyttelsestypen**: Denne ordre kan ikke konfigureres og er beskrevet i følgende tabel:

  <br>

  ****

  |Prioritet|Mailbeskyttelse|Kategori|Her kan du administrere|
  |---|---|---|---|
  |1|Malware|KAT:MALW|[Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md)|
  |2|Phishing|KAT:PHSH|[Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md)|
  |3|Spam med høj tillid|CAT:HSPM|[Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md)|
  |4|Spoofing|KAT:SPOOF|[Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Bruger efterligning (beskyttede brugere)|UIMP|[Konfigurer antiphishing-politikker i Microsoft Defender til Office 365](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Domænepersonation (beskyttede domæner)|DIMP|[Konfigurer antiphishing-politikker i Microsoft Defender til Office 365](configure-mdo-anti-phishing-policies.md)|
  |7|Spam|KAT:SPM|[Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md)|
  |8|Masse|KAT:MASSE|[Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md)|
  |

  <sup>\*</sup>Disse funktioner er kun tilgængelige i antiphishing-politikker i Microsoft Defender Office 365.

- **Politikkens** prioritet: For hver type politik (antispam, antimalware, antiphishing osv.) er der en standardpolitik, der gælder for alle, men du kan oprette brugerdefinerede politikker, der gælder for bestemte brugere. Hver brugerdefineret politik har en prioritetsværdi, der bestemmer den rækkefølge, politikkerne anvendes i. Standardpolitikken anvendes altid sidst.

  > [!IMPORTANT]
  > Hvis en bruger er defineret i flere politikker af samme type, er det kun politikken med højeste prioritet, der anvendes på dem. Eventuelle resterende politikker af den pågældende type evalueres ikke for brugeren (herunder standardpolitikken).

Overvej f.eks. følgende antiphishing-politikker i Microsoft Defender for Office 365, der gælder for de samme **brugere, og** en meddelelse, der identificeres som både bruger efterligning og spoofing:

<br>

****

|Politiknavn|Prioritet|Bruger efterligning|Antispoofing|
|---|---|---|---|
|Politik A|1|Til|Fra|
|Politik B|2|Fra|Til|
|

1. Meddelelsen markeres og behandles som spoof, fordi spoofing har en højere prioritet (4) end brugerens efterligning (5).
2. Politik A anvendes på brugerne, fordi den har en højere prioritet end politik B.
3. Baseret på indstillingerne i Politik A, sker der ikke noget med meddelelsen, fordi antispoofing er slået fra i politikken.
4. Behandling af politikker stopper, så politik B aldrig anvendes for brugerne.

Da det er muligt, at de samme brugere er med eller uden overlæg inkluderet i flere brugerdefinerede politikker af samme type, skal du bruge følgende designretningslinjer for brugerdefinerede politikker:

- Tildel en højere prioritet til politikker, der gælder for et lille antal brugere, og en lavere prioritet til politikker, der gælder for et stort antal brugere. Husk, at standardpolitikken altid anvendes sidst.
- Konfigurer dine politikker med højere prioritet, så de har strengere eller mere specialiserede indstillinger end politikker med lavere prioritet.
- Overvej at bruge færre brugerdefinerede politikker (brug kun brugerdefinerede politikker til brugere, der kræver mere restriktive eller mere specialiserede indstillinger).
