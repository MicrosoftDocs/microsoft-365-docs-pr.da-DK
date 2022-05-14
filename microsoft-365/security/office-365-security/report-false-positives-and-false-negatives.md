---
title: Rapportér falske positiver og falske negativer i Outlook
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
description: Få mere at vide om, hvordan du rapporterer falske positiver og falske negativer i Outlook ved hjælp af funktionen Rapportmeddelelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 762f16916e03940f4d0f95c48f13751d3cbd63c7
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416966"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Rapportér falske positiver og falske negativer i Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Hvis du er administrator i en Microsoft 365 organisation med Exchange Online postkasser, anbefaler vi, at du bruger siden **Indsendelser** på Microsoft 365 Defender-portalen. Du kan få flere oplysninger [under Brug portalen Indsendelser til at sende mistanke om spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

I Microsoft 365 organisationer med postkasser i Exchange Online eller lokale postkasser ved hjælp af hybrid moderne godkendelse kan du sende falske positiver (god mail, der blev blokeret eller sendt til mappen med uønsket post) og falske negativer (uønsket mail eller phish, der blev leveret til indbakken) til Exchange Online Protection (EOP).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil have den bedste brugerindsendelsesoplevelse, skal du bruge tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing.

- Tilføjelsesprogrammet Rapportmeddelelse og tilføjelsesprogrammet Rapport phishing fungerer for Outlook på alle platforme (Outlook på internettet, iOS, Android og Desktop).

- Hvis du er administrator i en organisation med Exchange Online postkasser, skal du bruge portalen Indsendelser på portalen Microsoft 365 Defender. Du kan få flere oplysninger under [Brug indsendelse af administratorer til at sende mistanke om spam, phish, URL-adresser og filer til Microsoft](admin-submission.md).

- Du kan konfigurere til at sende meddelelser direkte til Microsoft, en postkasse, du angiver, eller begge dele. Du kan få flere oplysninger under [Politikker for brugerindsendelser](user-submission.md).

- Du kan få flere oplysninger om, hvordan du henter og aktiverer tilføjelsesprogrammer til rapportmeddelelse eller phishing af rapporter, under [Aktivér rapportmeddelelsen eller tilføjelsesprogrammer til rapport phishing](enable-the-report-message-add-in.md).

- Du kan få flere oplysninger om rapportering af meddelelser til Microsoft under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

Se denne korte video for at få mere at vide om, hvordan du kan bruge Microsoft Defender for Office 365 til nemt at undersøge brugerindsendelser for at bestemme indholdet af en meddelelse og reagere på indsendelsen ved at anvende den relevante afhjælpningshandling. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBHof]

### <a name="turn-off-the-built-in-reporting-experience"></a>Slå den indbyggede rapporteringsoplevelse fra

Vi anbefaler ikke den indbyggede rapporteringsoplevelse i Outlook, fordi den ikke kan bruge [politikken for brugerindsendelse](./user-submission.md). Vi anbefaler, at du bruger tilføjelsesprogrammet Rapportmeddelelse eller tilføjelsesprogrammet Rapport phishing i stedet.

Du skal have tildelt tilladelser, før du kan køre denne cmdlet. Hvis du vil finde de tilladelser, der kræves for at køre en cmdlet eller parameter i din organisation, skal du se [Find de tilladelser, der kræves for at køre en Exchange cmdlet](/powershell/exchange/find-exchange-cmdlet-permissions).

Kør følgende PowerShell-kommando for at deaktivere den indbyggede rapporteringsoplevelse i Outlook på internettet:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```

## <a name="use-the-report-message-feature"></a>Brug funktionen Rapportmeddelelse

### <a name="report-junk-and-phishing-messages"></a>Rapportér uønskede meddelelser og phishingmeddelelser

I forbindelse med meddelelser i indbakken eller andre mailmapper undtagen uønsket mail skal du bruge følgende metode til at rapportere spam og phishing-meddelelser:

1. Vælg ellipsen **Flere handlinger** i øverste højre hjørne af den valgte meddelelse, vælg **Rapportmeddelelse** i rullemenuen, og vælg derefter **Uønsket** eller **Phishing**.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Ikonet Flere handlinger" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="Indstillingen Uønsket og phishing i ruden Rapportmeddelelse" lightbox="../../media/report-message-junk-phishing.png":::

2. De valgte meddelelser sendes til Microsoft til analyse og:
   - Flyttet til mappen Uønsket mail, hvis de blev rapporteret som spam.
   - Slettet, hvis de blev rapporteret som phishing.

### <a name="report-messages-that-are-not-junk"></a>Rapportmeddelelser, der ikke er uønsket

1. Vælg ellipsen **Flere handlinger** i øverste højre hjørne af den valgte meddelelse, vælg **Rapportmeddelelse** i rullemenuen, og vælg derefter **Ikke uønsket.**

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Ikonet, der indeholder flere handlinger" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="Indstillingen Ikke uønsket mail i ruden Rapportmeddelelse" lightbox="../../media/report-message-not-junk.png":::

2. Den valgte meddelelse sendes til Microsoft til analyse og flyttes til Indbakke eller en anden angivet mappe.

## <a name="view-and-review-reported-messages"></a>Få vist og gennemse rapporterede meddelelser

Hvis du vil gennemse meddelelser, som brugerne rapporterer til Microsoft, har du følgende muligheder:

- Brug siden **Indsendelser** på portalen Microsoft 365 Defender. Du kan få flere oplysninger under [Få vist brugerindsendelser til Microsoft](admin-submission.md#view-user-submissions-to-microsoft).
- Opret en regel for mailflow (også kendt som en transportregel) for at sende kopier af rapporterede meddelelser. Du kan finde instruktioner under [Brug regler for mailflow til at se, hvilke brugere der rapporterer til Microsoft](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
