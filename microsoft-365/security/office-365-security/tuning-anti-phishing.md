---
title: Finjuster beskyttelse mod phishing
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- MET150
description: Administratorer kan lære at identificere årsagerne til, hvorfor og hvordan en phishingmeddelelse kom igennem i Microsoft 365, og hvad de skal gøre for at forhindre flere phishingmeddelelser i fremtiden.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 299488a7ed8a891d870efb3ace618178c36552f1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588742"
---
# <a name="tune-anti-phishing-protection"></a>Finjuster beskyttelse mod phishing

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Selvom Microsoft 365 indeholder en række antiphishing-funktioner, der er aktiveret som standard, er det muligt, at nogle phishingmeddelelser stadig kan komme igennem til dine postkasser. I dette emne beskrives det, hvad du kan gøre for at finde ud af, hvorfor en phishingmeddelelse kom igennem, og hvad du kan gøre for at justere antiphishing-indstillingerne i din Microsoft 365-organisation uden ved et uheld at gøre tingene _værre_.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Det første, du skal gøre, er at håndtere eventuelle kompromitterede konti og sørge for, at du blokerer for, at flere phishing-meddelelser kommer igennem

Hvis en modtagers konto er blevet kompromitteret som et resultat af phishing-meddelelsen, skal du følge trinnene i Besvare en kompromitteret mailkonto [Microsoft 365](responding-to-a-compromised-email-account.md).

Hvis dit abonnement omfatter Microsoft Defender til Office 365, kan du bruge [Office 365 Threat Intelligence](office-365-ti.md) til at identificere andre brugere, som også har modtaget phishingmeddelelsen. Du har flere muligheder for at blokere phishingmeddelelser:

- [Pengeskab Links i Microsoft Defender til Office 365](set-up-safe-links-policies.md)

- [Pengeskab vedhæftede filer i Microsoft Defender til Office 365](set-up-safe-attachments-policies.md)

- [Antiphishing-politikker i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md). Bemærk, at du midlertidigt kan øge grænsen **for avanceret phishing** i politikken fra **Standard** til **Aggressive**, **Mere aggressive** eller **Mest aggressive**.

Bekræft, at Defender Office 365, at alle funktioner er slået til.

## <a name="report-the-phishing-message-to-microsoft"></a>Rapportér phishingmeddelelsen til Microsoft

Rapportering af phishingmeddelelser er nyttigt til justering af filtre, der bruges til at beskytte alle kunder Microsoft 365. Du kan finde en vejledning [i Rapportere meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>Undersøg brevhovederne i meddelelsen

Du kan undersøge overskrifterne i phishing-meddelelsen for at se, om der er noget, du selv kan gøre for at forhindre, at der kommer flere phishingmeddelelser igennem. Med andre ord kan gennemgangen af brevhovederne hjælpe dig med at identificere eventuelle indstillinger i din organisation, der var ansvarlige for at tillade phishingmeddelelserne.

Specifikt skal du markere overskriftsfeltet **X-Forefront Antispam Report** i brevhovederne for at finde indikationer af ignoreret filtrering for spam eller phishing i værdien SFV (Spam Filtering Apostram). Meddelelser, der springer `SCL:-1`filtrering over, har en post på , hvilket betyder, at en af dine indstillinger har tilladt denne meddelelse ved at tilsidesætte spam- eller phishingfrafald, der blev bestemt af tjenesten. Du kan finde flere oplysninger om, hvordan du får brevhoveder og en komplet liste over alle tilgængelige brevhoveder for uønsket post og phishing-meddelelser, under Brevhoveder for uønsket post [i Microsoft 365](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Bedste fremgangsmåder for at forblive beskyttet

- På månedsbasis skal du [køre Secure Score](../defender/microsoft-secure-score.md) for at vurdere din organisations sikkerhedsindstillinger.

- For meddelelser, der ender i karantæne ved en fejl, eller for meddelelser, der er tilladt igennem, anbefaler vi, at du søger efter disse meddelelser i Threat Explorer og registreringer [i realtid](threat-explorer.md). Du kan søge efter afsender, modtager eller meddelelses-id. Når du har fundet meddelelsen, kan du gå til detaljer ved at klikke på emnet. For en meddelelse, der er sat i karantæne, skal du se, hvad "registreringsteknologien" var, så du kan bruge den rette metode til at tilsidesætte. For en tilladt meddelelse kan du se, hvilken politik der gav meddelelsen tilladelse.

- Mail fra forfalskede afsendere (Meddelelsens Fra-adresse stemmer ikke overens med meddelelsens kilde) er klassificeret som phishing i Defender Office 365. Nogle gange er spoofing en god ide, og nogle gange ønsker brugere ikke, at meddelelser fra bestemte spoof-afsendere skal være i karantæne. For at minimere effekten for brugere skal du med jævne mellemrum gennemgå [spoof intelligence indsigt](learn-about-spoof-intelligence.md), fanen **Spoof** i lejerens [tilladelses-/](tenant-allow-block-list.md)[blokeringsliste og Spoof-registreringsrapporten](view-email-security-reports.md#spoof-detections-report). Når du har gennemset og blokeret forfalskede afsendere og foretaget de nødvendige tilsidesættelser, kan du have tillid til at konfigurere efterlignet intelligens i [antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings) til Karantæne mistænkelige meddelelser i stedet for at levere dem til brugerens mappe med Uønsket mail.

- Du kan gentage ovenstående trin for Repræsentation (domæne eller bruger) i Microsoft Defender for Office 365. Repræsentationsrapporten findes under Dashboard til **trusselsstyring** \> **Insights**\>.

- Gennemse med jævne mellemrum [statusrapporten for Trusselsbeskyttelse](view-reports-for-mdo.md#threat-protection-status-report).

- Nogle kunder tillader utilsigtet phishingmeddelelser ved at placere deres egne domæner på listen Tillad afsender eller Tillad domæne i antispam-politikker. Selvom denne konfiguration tillader adgang til nogle legitime meddelelser, tillader den også skadelige meddelelser, der normalt ville være blokeret af filtrene spam og/eller phishing. I stedet for at tillade domænet skal du rette det underliggende problem.

  Den bedste måde at håndtere legitime meddelelser, der blokeres af Microsoft 365 (falske positive), der involverer afsendere i dit domæne, er at konfigurere SPF-, DKIM- og DMARC-posterne fuldt ud i _DNS for alle_ dine maildomæner:

  - Kontrollér, at din SPF-post  identificerer alle kilder til mail for afsendere i dit domæne (glem ikke tredjepartstjenester!).

  - Brug hard fail (\-alle) til at sikre, at uautoriserede afsendere afvises af mailsystemer, der er konfigureret til at gøre dette. Du kan bruge [efterlignet](learn-about-spoof-intelligence.md) intelligensindsigt til at identificere afsendere, der bruger dit domæne, så du kan medtage autoriserede tredjepartsafsendere i din SPF-post.

  Du kan finde konfigurationsinstruktioner i:

  - [Konfigurer SPF for at forhindre spoofing](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md)

  - [Brug DMARC til at validere mail](use-dmarc-to-validate-email.md)

- Når det er muligt, anbefaler vi, at du leverer mails til dit domæne direkte Microsoft 365. Med andre ord kan du pege Microsoft 365 domænets MX-post mod Microsoft 365. Exchange Online Protection (EOP) kan give den bedste beskyttelse til dine skybrugere, når deres mail leveres direkte Microsoft 365. Hvis du skal bruge et system med mailadresser fra tredjepart foran EOP, skal du bruge Udvidet filtrering for forbindelser. Du kan finde en [vejledning under Udvidet filtrering for forbindelser i Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Brugerne skal bruge [tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md) eller tilføjelsesprogrammet [Report Phishing](enable-the-report-phish-add-in.md) til at rapportere meddelelser til Microsoft, som kan oplære vores system. Administratorer bør også drage fordel af [egenskaberne for administratorafsendelser](admin-submission.md) .

- Multi factor authentication (MFA) er en god måde at forhindre kompromitterede konti. Du bør på det kraftigste overveje at aktivere MFA for alle dine brugere. Hvis du ønsker en trinvis tilgang, skal du starte med at aktivere MFA for dine mest følsomme brugere (administratorer, ledere osv.), før du aktiverer MFA for alle. Du kan finde en vejledning [under Konfigurer multifaktorgodkendelse](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Regler for videresendelse til eksterne modtagere bruges ofte af hackere til at udtrække data. Brug oplysningerne **om gennemsyn af regler for videresendelse** af postkasse [i Microsoft Secure Score](../defender/microsoft-secure-score.md) til at finde og endda forhindre videresendelsesregler til eksterne modtagere. Du kan få mere at vide [under Ekstern videresendelse af klient-regler med Secure Score](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score).
