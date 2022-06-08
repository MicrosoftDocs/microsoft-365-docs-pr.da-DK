---
title: Hvad er forskellen mellem uønsket mail og massemail?
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
description: Administratorer kan få mere at vide om forskellene mellem uønsket mail (spam) og massemails (grå mail) i Exchange Online Protection (EOP).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dd876b522a0d565b84e8bb9043e277cd3bc34495
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940442"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>Hvad er forskellen mellem uønsket mail og massemail i EOP?

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365-organisationer med postkasser i Exchange Online eller eOP-organisationer (Exchange Online Protection) uden Exchange Online-postkasser spørger kunderne nogle gange: "Hvad er forskellen mellem uønsket mail og massemail?" I dette emne forklares forskellen, og de kontrolelementer, der er tilgængelige i EOP, beskrives.

- **Uønsket mail** er spam, som er uopfordrede og universelt uønskede meddelelser (når de identificeres korrekt). EOP afviser som standard spam baseret på kildemailserverens omdømme. Hvis en meddelelse overfører IP-kildens inspektion, sendes den til filtrering af spam. Hvis meddelelsen klassificeres som spam ved filtrering af spam, leveres meddelelsen (som standard) til de ønskede modtagere og flyttes til deres mappe med uønsket mail.

  - Du kan konfigurere de handlinger, der skal udføres på spamfiltreringsdomme. Du kan finde instruktioner under [Konfigurer politikker mod spam i EOP](configure-your-spam-filter-policies.md).

  - Hvis du er uenig i dommen om filtrering af spam, kan du rapportere meddelelser, som du anser for at være spam eller ikke-spam til Microsoft på flere måder, som beskrevet i [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

- **Massemail** (også kendt som _grå mail_) er sværere at klassificere. Mens spam er en konstant trussel, massemail er ofte engangsannoncer eller marketingmeddelelser. Nogle brugere ønsker massemails (og faktisk har de bevidst tilmeldt sig for at modtage dem), mens andre brugere anser massemail for at være spam. Nogle brugere ønsker f.eks. at modtage reklamemeddelelser fra Contoso Corporation eller invitationer til en kommende konference om cybersikkerhed, mens andre brugere anser de samme meddelelser for at være spam.

  Du kan få flere oplysninger om, hvordan massemails identificeres, [under Samlet klageniveau (BCL) i EOP](bulk-complaint-level-values.md).

## <a name="how-to-manage-bulk-email"></a>Sådan administrerer du massemail

På grund af den blandede reaktion på massemails er der ikke en universel vejledning, der gælder for alle organisationer.

Anti-spam-politi har en standard-BCL-grænse, der bruges til at identificere massemail som spam. Administratorer kan øge eller mindske tærsklen. Du kan få flere oplysninger i følgende emner:

- [Konfigurer politikker for spam i EOP](configure-your-spam-filter-policies.md).

- [Politikindstillinger for EOP-antispam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

En anden mulighed, der er let at overse: Hvis en bruger klager over at modtage massemail, men meddelelserne er fra velansete afsendere, der sender spamfiltrering i EOP, skal brugeren kontrollere, om der er en mulighed for at opsige abonnementet i massemailmeddelelsen.
