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
description: Administratorer kan få mere at vide om, hvorfor og hvordan en phishing-meddelelse kom igennem i Microsoft 365, og hvad de skal gøre for at forhindre flere phishing-meddelelser i fremtiden.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7c39d3f4b3ee6fb98cadcd5518a81710402c1cb3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647749"
---
# <a name="tune-anti-phishing-protection"></a>Finjuster beskyttelse mod phishing

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Selvom Microsoft 365 leveres med en række anti-phishing-funktioner, der er aktiveret som standard, er det muligt, at nogle phishing-meddelelser stadig kan komme igennem til dine postkasser. I dette emne beskrives det, hvad du kan gøre for at finde ud af, hvorfor en phishing-meddelelse kom igennem, og hvad du kan gøre for at justere indstillingerne for anti-phishing i din Microsoft 365 organisation _uden at komme til at gøre tingene værre ved et uheld_.

## <a name="first-things-first-deal-with-any-compromised-accounts-and-make-sure-you-block-any-more-phishing-messages-from-getting-through"></a>Første ting først: Tag dig af alle kompromitterede konti, og sørg for, at du blokerer flere phishing-meddelelser fra at komme igennem

Hvis en modtagers konto blev kompromitteret som følge af phishing-meddelelsen, skal du følge trinnene i [Besvarelse af en kompromitteret mailkonto i Microsoft 365](responding-to-a-compromised-email-account.md).

Hvis dit abonnement indeholder Microsoft Defender for Office 365, kan du bruge [Office 365 Threat Intelligence](office-365-ti.md) til at identificere andre brugere, der også har modtaget phishing-meddelelsen. Du har flere muligheder for at blokere phishing-meddelelser:

- [Pengeskab Links i Microsoft Defender for Office 365](set-up-safe-links-policies.md)

- [Pengeskab vedhæftede filer i Microsoft Defender for Office 365](set-up-safe-attachments-policies.md)

- [Politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md). Bemærk, at du midlertidigt kan øge **tærsklerne for avanceret phishing** i politikken fra **Standard** til **Aggressiv**, **Mere aggressiv** eller **Mest aggressiv**.

Kontrollér, at disse Defender for Office 365 funktioner er slået til.

## <a name="report-the-phishing-message-to-microsoft"></a>Rapportér phishingmeddelelsen til Microsoft

Det er nyttigt at rapportere phishing-meddelelser, når du skal justere de filtre, der bruges til at beskytte alle kunder i Microsoft 365. Du kan finde instruktioner under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="inspect-the-message-headers"></a>Undersøg brevhovederne

Du kan undersøge overskrifterne i phishing-meddelelsen for at se, om der er noget, du selv kan gøre for at forhindre, at der kommer flere phishing-meddelelser. Det vil sige, at hvis du undersøger brevhovederne, kan det hjælpe dig med at identificere de indstillinger i organisationen, der er ansvarlige for at tillade phishing-meddelelserne.

Du skal specifikt kontrollere feltet **X-Forefront-Antispam-Report-header** i meddelelsesheaderne for at få oplysninger om, at filtrering af spam eller phishing springes over, i SFV-værdien (Spam Filtering Verdict). Meddelelser, der springer filtrering over, har adgang til `SCL:-1`, hvilket betyder, at en af dine indstillinger tillader denne meddelelse ved at tilsidesætte de spam- eller phishing-domme, der blev bestemt af tjenesten. Du kan få flere oplysninger om, hvordan du henter brevhoveder og den komplette liste over alle tilgængelige headere til anti-spam og anti-phishing-meddelelser, [under Brevhoveder til anti-spam i Microsoft 365](anti-spam-message-headers.md).

## <a name="best-practices-to-stay-protected"></a>Bedste praksis for beskyttelse

- Kør [Secure Score](../defender/microsoft-secure-score.md) hver måned for at vurdere din organisations sikkerhedsindstillinger.

- For meddelelser, der ender i karantæne ved en fejl, eller for meddelelser, der er tilladt gennem, anbefaler vi, at du søger efter disse meddelelser i [Threat Explorer og registreringer i realtid](threat-explorer.md). Du kan søge efter afsender, modtager eller meddelelses-id. Når du har fundet meddelelsen, skal du gå til detaljer ved at klikke på emnet. Hvis du har en meddelelse i karantæne, skal du se, hvad "registreringsteknologien" var, så du kan bruge den relevante metode til at tilsidesætte. Hvis du vil se en tilladt meddelelse, skal du se, hvilken politik der tillader meddelelsen.

- Mail fra spoofed afsendere (fra-adressen på meddelelsen stemmer ikke overens med kilden til meddelelsen) klassificeres som phishing i Defender for Office 365. Nogle gange er spoofing godartet, og nogle gange ønsker brugerne ikke, at meddelelser fra en bestemt spoofed afsender sættes i karantæne. Hvis du vil minimere indvirkningen for brugerne, skal du jævnligt gennemse [indsigten spoof intelligence](learn-about-spoof-intelligence.md), fanen **Spoof** på [listen Over tilladte/blokerede lejere](tenant-allow-block-list.md) og [rapporten Spoof-registreringer](view-email-security-reports.md#spoof-detections-report). Når du har gennemgået tilladte og blokerede spoofed afsendere og foretaget de nødvendige tilsidesættelser, kan du være sikker på at [konfigurere spoof intelligence i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#spoof-settings) for at sætte mistænkelige meddelelser i **karantæne** i stedet for at levere dem til brugerens mappe med uønsket mail.

- Du kan gentage ovenstående trin for repræsentation (domæne eller bruger) i Microsoft Defender for Office 365. Repræsentationsrapporten findes under **Dashboard** \> til **trusselsadministration** \> **Insights**.

- Gennemse [rapporten Status for trusselsbeskyttelse](view-reports-for-mdo.md#threat-protection-status-report) periodisk.

- Nogle kunder tillader utilsigtet phishing-meddelelser ved at placere deres egne domæner på listen Tillad afsender eller Tillad domæne i politikker til bekæmpelse af spam. Selvom denne konfiguration tillader nogle legitime meddelelser, tillader den også skadelige meddelelser, der normalt blokeres af spam- og/eller phishingfiltrene. I stedet for at tillade domænet skal du rette det underliggende problem.

  Den bedste måde at håndtere legitime meddelelser, der er blokeret af Microsoft 365 (falske positiver), der involverer afsendere i dit domæne, er at konfigurere SPF-, DKIM- og DMARC-posterne fuldt ud og fuldstændigt i DNS for _alle_ dine maildomæner:

  - Bekræft, at din SPF-post identificerer _alle_ mailkilder for afsendere i dit domæne (glem ikke tredjepartstjenester!).

  - Brug hård fejl (\-alle) for at sikre, at uautoriserede afsendere afvises af mailsystemer, der er konfigureret til at gøre det. Du kan bruge [indsigt i spoof intelligence](learn-about-spoof-intelligence.md) til at identificere afsendere, der bruger dit domæne, så du kan inkludere godkendte afsendere fra tredjepart i din SPF-post.

  Du kan finde konfigurationsanvisninger under:

  - [Konfigurer SPF for at forhindre forfalskning](set-up-spf-in-office-365-to-help-prevent-spoofing.md)

  - [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md)

  - [Brug DMARC til at validere mail](use-dmarc-to-validate-email.md)

- Når det er muligt, anbefaler vi, at du leverer mail til dit domæne direkte til Microsoft 365. Peg med andre ord MX-posten for dit Microsoft 365 domæne for at Microsoft 365. Exchange Online Protection (EOP) er i stand til at yde den bedste beskyttelse til dine cloudbrugere, når deres mail leveres direkte til Microsoft 365. Hvis du skal bruge et tredjeparts-e-mailhygiejnesystem foran EOP, skal du bruge forbedret filtrering for forbindelser. Du kan finde instruktioner [under Udvidet filtrering for forbindelser i Exchange Online](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- Brugerne skal bruge [tilføjelsesprogrammet Rapportmeddelelse](enable-the-report-message-add-in.md) eller [tilføjelsesprogrammet Rapport phishing](enable-the-report-phish-add-in.md) til at rapportere meddelelser til Microsoft, som kan oplære vores system. Administratorer bør også drage fordel af [Administration indsendelsesfunktioner](admin-submission.md).

- Multifaktorgodkendelse (MFA) er en god måde at forhindre kompromitterede konti på. Du bør på det kraftigste overveje at aktivere MFA for alle dine brugere. I forbindelse med en faseinddelt tilgang skal du starte med at aktivere MFA for dine mest følsomme brugere (administratorer, direktører osv.), før du aktiverer MFA for alle. Du kan finde instruktioner under [Konfigurer multifaktorgodkendelse](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

- Videresendelsesregler til eksterne modtagere bruges ofte af hackere til at udtrække data. Brug oplysninger om **regler for videresendelse af postkasser** i [Microsoft Secure Score](../defender/microsoft-secure-score.md) til at finde og endda forhindre videresendelse af regler til eksterne modtagere. Du kan få flere oplysninger under [Mitigating Client External Forwarding Rules with Secure Score (Mitigating Client External Forwarding Rules with Secure Score](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score)).
