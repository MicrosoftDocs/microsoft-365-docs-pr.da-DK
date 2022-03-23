---
title: Sikkerhedsanbefalinger for prioritetskonti i Microsoft 365, prioritetskonti, prioritetskonti i Office 365, prioritetskonti Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-protecthve
ms.custom: ''
description: Administratorer kan lære, hvordan de hæver sikkerhedsindstillingerne og bruger rapporter, beskeder og undersøgelser til prioritetskonti i deres Microsoft 365 organisationer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2e0964d9b023a3a7c1efdda121cc34c1f37edd06
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63590488"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Sikkerhedsanbefalinger for prioritetskonti i Microsoft 365

Ikke alle brugerkonti har adgang til de samme firmaoplysninger. Nogle konti har adgang til følsomme oplysninger, f.eks. finansielle data, oplysninger om produktudvikling, partneradgang til vigtige buildsystemer og meget mere. Hvis de kompromitteres, udgør konti, der har adgang til meget fortrolige oplysninger, en alvorlig trussel. Vi kalder disse typer konti for _prioritetskonti_. Prioritetskonti omfatter (men er ikke begrænset til) COS, CISOs, CFOs, infrastrukturadministratorkonti, opbygge systemkonti og meget mere.

For hackere er almindelige phishing-angreb, der viser et tilfældigt net for almindelige eller ukendte brugere, ineffektiv. Derimod er phishing-phishing _eller_ _whaling-angreb_ , der målrettes efter prioritet, meget berigende for hackere. Prioritetskonti kræver således stærkere end almindelig beskyttelse for at forhindre, at kontoen bliver kompromitteret.

Microsoft 365 og Microsoft Defender til Office 365 indeholder flere vigtige funktioner, som giver ekstra lag af sikkerhed til dine prioritetskonti. I denne artikel beskrives disse funktioner, og hvordan de bruges.

![Oversigt over sikkerhedsanbefalinger i ikonform.](../../media/security-recommendations-for-priority-users.png)

<br>

****

|Opgave|Alle Office 365 Enterprise-planer|Microsoft 365 E3|Microsoft 365 E5|
|---|:---:|:---:|:---:|
|[Øg sikkerheden for logon på prioritetskonti](#increase-sign-in-security-for-priority-accounts)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Brug faste, forudindstillede sikkerhedspolitikker til prioritetskonti](#use-strict-preset-security-policies-for-priority-accounts)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Anvend brugermærker på prioritetskonti](#apply-user-tags-to-priority-accounts)|||![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Overvåge prioritetskonti i beskeder, rapporter og registreringer](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Oplære brugere](#train-users)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|

> [!NOTE]
> Du kan finde oplysninger om _beskyttelse af privilegerede_ konti (administratorkonti) [i dette emne](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="increase-sign-in-security-for-priority-accounts"></a>Øg sikkerheden for logon på prioritetskonti

Prioritetskonti kræver øget logonsikkerhed. Du kan øge deres logonsikkerhed ved at kræve Multi-Factor Authentication (MFA) og deaktivere ældre godkendelsesprotokoller.

Du kan finde en vejledning [under Trin 1. Øg sikkerheden for logon for eksterne medarbejdere med MFA](../../solutions/empower-people-to-work-remotely-secure-sign-in.md). Selvom denne artikel handler om eksterne medarbejdere, gælder de samme begreber for prioritetsbrugere.

**Bemærk**! Vi anbefaler på det kraftigste, at du globalt deaktiverer ældre godkendelsesprotokoller for alle brugere med prioritet, som beskrevet i den forrige artikel. Hvis dine forretningskrav forhindrer dig i at gøre dette, Exchange Online følgende kontrolelementer for at begrænse omfanget af ældre godkendelsesprotokoller:

- Du kan bruge [](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) godkendelsespolitikker og [](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) klientadgangsregler i Exchange Online til at blokere eller tillade grundlæggende godkendelse og ældre godkendelsesprotokoller som POP3, IMAP4 og godkendt SMTP for bestemte brugere.

- Du kan deaktivere adgang til POP3 og IMAP4 for individuelle postkasser. Du kan deaktivere godkendt SMTP på organisationsniveau og aktivere den i bestemte postkasser, hvor den stadig skal bruges. Du kan finde instruktioner i følgende artikler:
  - [Aktivere eller deaktivere pop3- eller IMAP4-adgang for en bruger](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Aktivere eller deaktivere godkendt SMTP-klientindsendelse (SMTP AUTH)](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

Det er også værd at bemærke, at grundlæggende godkendelse er ved at blive frarådet i Exchange Online til Exchange Web Services (EWS), Exchange ActiveSync, POP3, IMAP4 og Remote PowerShell. Du kan finde flere oplysninger i dette [blogindlæg](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Brug faste, forudindstillede sikkerhedspolitikker til prioritetskonti

Prioritetsbrugere kræver strengere handlinger for de forskellige beskyttelser, der er tilgængelige i Exchange Online Protection (EOP) og Defender til Office 365.

I stedet for at levere meddelelser, der er klassificeret som spam, til mappen Uønsket mail, skal du f.eks. sætte de samme meddelelser i karantæne, hvis de er beregnet til prioritetskonti.

Du kan implementere denne restriktive fremgangsmåde for prioritetskonti ved hjælp af profilen Streng i forudindstillede sikkerhedspolitikker.

Forudindstillede sikkerhedspolitikker er et praktisk og centralt sted til at anvende vores anbefalede strenge politikindstillinger for alle beskyttelser i EOP og Defender Office 365. Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md).

Hvis du vil have mere at vide om, hvordan indstillingerne For restriktiv politik adskiller sig fra standard- og standardpolitikindstillingerne, skal du se Anbefalede indstillinger [for EOP og Microsoft Defender Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

## <a name="apply-user-tags-to-priority-accounts"></a>Anvend brugermærker på prioritetskonti

Brugermærker i Microsoft Defender til Office 365 Plan 2 (som en del af Microsoft 365 E5 eller et tilføjelsesabonnement) er en metode til hurtigt at identificere og klassificere bestemte brugere eller grupper af brugere i rapporter og hændelsesundersøgelse.

**Prioritetskonti** er en type indbygget brugerkode (kaldet et _systemmærke_), som du kan bruge til at identificere hændelser og beskeder, der involverer prioritetskonti. Du kan finde flere oplysninger **om prioritetskonti** [under Administrere og overvåge prioritetskonti](../../admin/setup/priority-accounts.md).

Du kan også oprette brugerdefinerede mærker til yderligere at identificere og klassificere dine prioritetskonti. Du kan få mere at vide [under Brugermærker](user-tags.md). Du kan administrere **prioritetskonti** (systemmærker) i samme grænseflade som brugerdefinerede brugermærker.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Overvåge prioritetskonti i beskeder, rapporter og registreringer

Når du sikrer og mærker dine prioritetsbrugere, kan du bruge de tilgængelige rapporter, beskeder og undersøgelser i EOP og Defender til Office 365 til hurtigt at identificere hændelser eller registreringer, der involverer prioritetskonti. De funktioner, der understøtter brugermærker, er beskrevet i følgende tabel.

<br>

****

|Funktion|Beskrivelse|
|---|---|
|Beskeder|Brugermærkerne for de berørte brugere er synlige og tilgængelige som filtre **på siden Beskeder** i Microsoft 365 Defender portal. Du kan få mere at vide [under Få vist beskeder](../../compliance/alert-policies.md#viewing-alerts).|
|Stifinder <p> Registreringer i realtid|I **Explorer** (Defender til Office 365 Plan 2) eller registreringer i realtid (Defender til Office 365 Plan 1) er brugermærker synlige i gittervisningen Mail og pop **op-vinduet** Mailoplysninger. Brugermærker er også tilgængelige som en egenskab, der kan filtreres. Du kan få mere at vide  [under Mærker i Stifinder](threat-explorer.md#tags-in-threat-explorer).|
|Kampagnevisninger|Brugermærker er en af mange filtrerbare egenskaber i Kampagnevisninger i Microsoft Defender Office 365 Plan 2. Du kan finde flere oplysninger i [Kampagnevisninger](campaigns.md).|
|Statusrapport over trusselsbeskyttelse|I stort set alle visninger og detaljetabeller i **statusrapporten for trusselsbeskyttelse** kan du filtrere resultaterne efter **prioritetskonti**. Du kan få mere at vide [under Statusrapport for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).|
|Mailproblemer for prioritetskonti-rapport|Rapporten **Mailproblemer for prioritetskonti** i Exchange Administration (EAC) indeholder oplysninger om ikke-leveret og forsinkede meddelelser for **prioritetskonti**. Få mere at vide under [Mailproblemer for prioritetskonti-rapport](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).|
|

## <a name="train-users"></a>Oplære brugere

Kursus brugere med prioritetskonti kan hjælpe med at spare disse brugere og dit sikkerhedsteam meget tid og frustration. Erfarne brugere er mindre tilbøjelige til at åbne vedhæftede filer eller klikke på links i tvivlsomme mails, og de er mere tilbøjelige til at undgå mistænkelige websteder.

The Harvard The School [Cybersecurity Campaign Handbook giver](https://www.belfercenter.org/CyberPlaybook) fremragende vejledning til oprettelse af en stærk kultur for sikkerhedskultur i din organisation, herunder uddannelse af brugere til at identificere phishing-angreb.

Microsoft 365 indeholder følgende ressourcer, som kan hjælpe med at informere brugerne i organisationen:

<br>

****

|Koncept|Ressourcer|Beskrivelse|
|---|---|---|
|Microsoft 365|[Brugerdefinerbare læringsstier](/office365/customlearning/)|Disse ressourcer kan hjælpe dig med at sammensætte kurser til brugere i organisationen.|
|Microsoft 365 sikkerhed|[Learning modul: Beskyt din organisation med indbygget, intelligent sikkerhed Microsoft 365](/learn/modules/security-with-microsoft-365)|Dette modul gør det muligt for dig at beskrive, Microsoft 365 sikkerhedsfunktioner fungerer sammen, og til at fordele ved disse sikkerhedsfunktioner.|
|Multifaktorgodkendelse|[Totrinsbekræftelse: Hvad er den ekstra bekræftelsesside?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|Denne artikel hjælper slutbrugere med at forstå, hvad multifaktorgodkendelse er, og hvorfor den bruges i din organisation.|
|Kursus i angrebssimulering|[Kom i gang med at bruge simuleringskursus til angreb](attack-simulation-training-get-started.md)|Kursus i angrebssimulering i Microsoft Defender Office 365 Plan 2 giver administrator mulighed for at konfigurere, starte og spore simulerede phishingangreb mod bestemte grupper af brugere.|

Desuden anbefaler Microsoft, at brugerne gør de handlinger, der er beskrevet i denne artikel: [Beskyt din konto og dine enheder mod hackere og malware](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Disse handlinger omfatter:

- Brug af stærke adgangskoder
- Beskyttelse af enheder
- Aktivering af sikkerhedsfunktioner på Windows og Mac-pc'er (for enheder, der ikke er administrerede)

## <a name="see-also"></a>Se også

[Vi annoncerer Prioritetskontobeskyttelse i Microsoft Defender Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
