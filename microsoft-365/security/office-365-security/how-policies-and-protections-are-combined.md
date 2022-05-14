---
title: Rækkefølgen og rækkefølgen af mailbeskyttelse
keywords: sikkerhed, malware, Microsoft 365, M365, Security Center, Microsoft 365 Defender portal, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Identity
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
description: Administratorer kan få mere at vide om beskyttelsesrækkefølgen i Exchange Online Protection (EOP), og hvordan prioritetsværdien i beskyttelsespolitikker bestemmer, hvilken politik der anvendes.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8b7bf48de0939ec913982feb399b38dc2c540157
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417748"
---
# <a name="order-and-precedence-of-email-protection"></a>Rækkefølgen og rækkefølgen af mailbeskyttelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser, kan indgående mails være markeret med flere former for beskyttelse. Det kan f.eks. være de indbyggede politikker til bekæmpelse af phishing i EOP, der er tilgængelige for alle Microsoft 365 kunder, og de mere robuste politikker til bekæmpelse af phishing, der er tilgængelige for Microsoft Defender for Office 365 kunder. Meddelelser passerer også gennem flere registreringsscanninger for malware, spam, phishing osv. På grund af al denne aktivitet kan der være en vis forvirring om, hvilken politik der anvendes.

Generelt identificeres en politik, der anvendes på en meddelelse, i **headeren X-Forefront-Antispam-Report** i egenskaben **CAT (Category).** Du kan få flere oplysninger under [Brevhoveder til anti-spam](anti-spam-message-headers.md).

Der er to vigtige faktorer, der bestemmer, hvilken politik der anvendes på en meddelelse:

- **Behandlingsrækkefølgen for mailbeskyttelsestypen**: Denne rækkefølge kan ikke konfigureres, og den er beskrevet i følgende tabel:

  |Rækkefølge|Mailbeskyttelse|Kategori|Hvor skal du administrere?|
  |:---:|---|---|---|
  |1|Malware|CAT:MALW|[Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md)|
  |2|Phishing|CAT:PHSH|[Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md)|
  |3|Spam med høj genkendelsessikkerhed|CAT:HSPM|[Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md)|
  |4|Spoofing|CAT:SPOOF|[Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md)|
  |5<sup>\*</sup>|Repræsentation af brugere (beskyttede brugere)|UIMP|[Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md)|
  |6<sup>\*</sup>|Repræsentation af domæne (beskyttede domæner)|DIMP|[Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md)|
  |7|Spam|CAT:SPM|[Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md)|
  |8|Bulk|CAT:BULK|[Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md)|

  <sup>\*</sup>Disse funktioner er kun tilgængelige i politikker til bekæmpelse af phishing i Microsoft Defender for Office 365.

- **Prioriteten for politikken**: For hver type politik (anti-spam, anti-malware, anti-phishing osv.) er der en standardpolitik, der gælder for alle, men du kan oprette brugerdefinerede politikker, der gælder for bestemte brugere (modtagere). Hver brugerdefineret politik har en prioritetsværdi, der bestemmer den rækkefølge, som politikkerne anvendes i. Standardpolitikken anvendes altid sidst.

  > [!IMPORTANT]
  > Hvis en modtager er defineret i flere politikker af samme type (anti-spam, anti-phishing osv.), er det kun politikken med den højeste prioritet, der anvendes på modtageren. Eventuelle resterende politikker af denne type evalueres ikke for modtageren (herunder standardpolitikken).

Overvej f.eks. følgende **anti-phishing-politikker** i Microsoft Defender for Office 365 **, der gælder for de samme brugere**, og en meddelelse, der er identificeret som **både brugerrepræsentation og spoofing**:

|Politiknavn|Prioritet|Bruger repræsenter|Anti-spoofing|
|---|:---:|:---:|:---:|
|Politik A|1|På|Ud|
|Politik B|2|Ud|På|

1. Meddelelsen identificeres som spoofing, fordi spoofing (4) evalueres før brugerrepræsentation (5).
2. Politik A anvendes først, fordi den har en højere prioritet end Politik B.
3. På baggrund af indstillingerne i Politik A udføres der ingen handling på meddelelsen, fordi anti-spoofing er slået fra.
4. Behandlingen af anti-phishing-politikker stopper for alle inkluderede modtagere, så Politik B anvendes aldrig på modtagere, der også er i Politik A.

Da de samme brugere bevidst eller utilsigtet er inkluderet i flere politikker af samme type, skal du bruge følgende retningslinjer for design for brugerdefinerede politikker:

- Tildel en højere prioritet til politikker, der gælder for et lille antal brugere, og en lavere prioritet til politikker, der gælder for et stort antal brugere. Husk, at standardpolitikken altid anvendes sidst.
- Konfigurer dine politikker med højere prioritet for at have strengere eller mere specialiserede indstillinger end politikker med lavere prioritet.
- Overvej at bruge færre brugerdefinerede politikker (brug kun brugerdefinerede politikker for brugere, der kræver strengere eller mere specialiserede indstillinger).
