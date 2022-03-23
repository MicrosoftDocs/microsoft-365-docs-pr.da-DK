---
title: Hvad&apos; er forskellen på uønsket mail og massemails?
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
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om forskellene mellem uønsket mail (spam) og massemail (grå mail) i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e8a896ac3360ccf799dbe34c7e298f76140ee6d5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587311"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Hvad er forskellen på uønsket mail og massemail i EOP?

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser, spørger kunder nogle gange: "Hvad er forskellen på uønsket mail og massemail?" I dette emne beskrives forskellen, og de kontrolelementer, der er tilgængelige i EOP, beskrives.

- **Uønsket mail** er spam, som er uopfordrede og uønskede meddelelser (når de identificeres korrekt). Som standard afviser EOP spam på baggrund af omdømmet fra kildemailserveren. Hvis en meddelelse videregiver kilde-IP-inspektion, sendes den til spamfiltrering. Hvis meddelelsen er klassificeret som spam af spamfiltrering, leveres meddelelsen (som standard) til de tilsigtede modtagere og flyttes til mappen Uønsket mail.

  - Du kan konfigurere de handlinger, der skal for at gøre noget ved spamfiltrering. Du kan finde en vejledning [under Konfigurer antispam-politikker i EOP](configure-your-spam-filter-policies.md).

  - Hvis du er uenig i vores vurdering af spamfiltrering, kan du rapportere meddelelser, som du mener er spam eller ikke-spam, til Microsoft på flere måder, som beskrevet i Rapportere meddelelser og filer til [Microsoft](report-junk-email-messages-to-microsoft.md).

- **Massemails** (også kaldet _grå mail_) er sværere at klassificere. Mens spam er en konstant trussel, er massemails ofte engangsannoncer eller marketingmeddelelser. Nogle brugere ønsker massemails (og faktisk har de bevidst tilmeldt sig at modtage dem), mens andre brugere anser massemails som spam. Eksempelvis vil nogle brugere modtage reklamemeddelelser fra Contoso Corporation eller invitationer til en kommende konference om cybersikkerhed, mens andre brugere anser de samme meddelelser for at være spam.

  Du kan finde flere oplysninger om, hvordan massemails identificeres, under Niveauet [af masseklager (BCL) i EOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Sådan administrerer du massemails

På grund af den blandede reaktion på massemails er der ikke universel vejledning, der gælder for alle organisationer.

Antispam-politik har en standard BCL-grænseværdi, der bruges til at identificere massemail som spam. Administratorer kan øge eller mindske grænseværdien. Du kan finde flere oplysninger i følgende emner:

- [Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md).

- [Indstillinger for EOP-antispampolitik](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

En anden mulighed, der er nem at overse: Hvis en bruger beklager sig over at modtage massemails, men meddelelserne er velrenommerede afsendere, der passerer spamfiltrering i EOP, skal du bede brugeren om at kontrollere, om der er en indstilling for frameldning i massemailen.
