---
title: Rapportér falske positive og falske negativer i Outlook
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan du rapporterer falske positive og falske Outlook ved hjælp af funktionen Rapportmeddelelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f2181df44f8d193f8c19c508451733773bd20708
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473498"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Rapportér falske positive og falske negativer i Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Hvis du er administrator i en Microsoft 365 organisation med Exchange Online-postkasser, anbefaler vi, at du bruger siden Indsendelser på Microsoft 365 Defender-portalen. Få mere at vide under [Brug portalen indsendelser til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

I Microsoft 365-organisationer med postkasser i Exchange Online eller lokale postkasser med moderne hybridgodkendelse kan du sende falske positive (god mail, der blev blokeret eller sendt til mappen Uønsket) og falske negativer (uønsket mail eller phish, der blev leveret til indbakken) til Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du får den bedste brugerindsendelsesoplevelse ved at bruge tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapportphishing.

- Tilføjelsesprogrammet Rapportmeddelelse og tilføjelsesprogrammet Report Phishing fungerer for Outlook på alle platforme (Outlook på internettet, iOS, Android og skrivebord).

- Hvis du er administrator i en organisation med Exchange Online, kan du bruge indsendelsesportalen på Microsoft 365 Defender portal. Få mere at vide under [Brug administratorindsendelse til at sende mistænkeligt spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

- Du kan konfigurere at sende meddelelser direkte til Microsoft, en postkasse, du angiver, eller begge dele. Få mere at vide under [Politikker for brugerindsendelse](user-submission.md).

- Du kan finde flere oplysninger om, hvordan du henter og aktiverer rapportmeddelelsen eller tilføjelsesprogrammet Report Phishing, under Aktivere rapportmeddelelsen eller tilføjelsesprogrammet [Rapportphishing](enable-the-report-message-add-in.md).

- Du kan finde flere oplysninger om rapportering af meddelelser til Microsoft [i Rapportere meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

### <a name="turn-off-the-built-in-reporting-experience"></a>Slå den indbyggede rapporteringsoplevelse fra

Vi anbefaler ikke den indbyggede rapporteringsoplevelse i Outlook fordi den ikke kan bruge politikken for [brugerindsendelse](./user-submission.md). Vi anbefaler, at du i stedet bruger tilføjelsesprogrammet Rapportmeddelelse eller phishing-tilføjelsesprogrammet Rapport.

Du skal have tildelt tilladelser, før du kan køre denne cmdlet. For at finde de tilladelser, der kræves for at køre en cmdlet eller parameter i din organisation, skal du se Find de nødvendige tilladelser til at køre en Exchange [cmdlet](/powershell/exchange/find-exchange-cmdlet-permissions).

Kør følgende PowerShell-kommando for at deaktivere den indbyggede rapporteringsoplevelse i Outlook på internettet:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```


## <a name="use-the-report-message-feature"></a>Brug funktionen Rapportmeddelelse

### <a name="report-junk-and-phishing-messages"></a>Rapportér uønskede meddelelser og phishingmeddelelser

For meddelelser i indbakken eller en anden mailmappe, undtagen Uønsket mail, skal du bruge følgende metode til at rapportere spam- og phishingmeddelelser:

1. Vælg **ellipserne** Flere handlinger i øverste højre hjørne af den markerede meddelelse, vælg Rapportmeddelelse i rullemenuen, og vælg derefter **Uønsket** eller **Phishing**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Ikonet Flere handlinger" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="Indstillingen Uønsket og phishing i ruden Rapportmeddelelse" lightbox="../../media/report-message-junk-phishing.png":::

2. De valgte meddelelser sendes til Microsoft til analyse og:
   - Flyttet til mappen Uønsket mail, hvis de blev rapporteret som spam.
   - Slettet, hvis det blev rapporteret som phishing.

### <a name="report-messages-that-are-not-junk"></a>Rapportér meddelelser, der ikke er uønskede

1. Vælg **ellipserne** Flere handlinger i øverste højre hjørne af den markerede meddelelse, vælg Rapportmeddelelse i rullemenuen, og vælg derefter **Ikke uønsket**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Ikonet, der indeholder flere handlinger" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="Indstillingen Ikke uønsket under ruden Rapportmeddelelse" lightbox="../../media/report-message-not-junk.png":::

2. Den markerede meddelelse sendes til Microsoft til analyse og flyttes til Indbakke eller en anden angivet mappe.

## <a name="view-and-review-reported-messages"></a>Få vist og gennemse rapporterede meddelelser

Hvis du vil gennemse meddelelser, som brugerne rapporterer til Microsoft, har du følgende muligheder:

- Brug **siden Indsendelser** i Microsoft 365 Defender portal. Få mere at vide under [Få vist brugerindsendelser til Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- Opret en regel for mailflow (også kaldet en transportregel) til at sende kopier af rapporterede meddelelser. Du kan finde en vejledning [i Brug regler for mailflow for at se, hvad brugerne rapporterer til Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
