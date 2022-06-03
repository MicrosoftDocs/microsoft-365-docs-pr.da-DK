---
title: Sikkerhedsanbefalinger for prioritetskonti i Microsoft 365, prioritetskonti, prioritetskonti i Office 365, prioritetskonti i Microsoft 365
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
description: Administratorer kan få mere at vide om, hvordan de hæver sikkerhedsindstillingerne og bruger rapporter, beskeder og undersøgelser til prioriterede konti i deres Microsoft 365 organisationer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 99e4726af1226e044715d33e92a176c9292b49ab
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873374"
---
# <a name="security-recommendations-for-priority-accounts-in-microsoft-365"></a>Sikkerhedsanbefalinger for prioritetskonti i Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for:**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Det er ikke alle brugerkonti, der har adgang til de samme firmaoplysninger. Nogle konti har adgang til følsomme oplysninger, f.eks. finansielle data, produktudviklingsoplysninger, partneradgang til kritiske buildsystemer m.m. Hvis de kompromitteres, udgør konti, der har adgang til meget fortrolige oplysninger, en alvorlig trussel. Vi kalder disse typer konti _prioritetskonti_. Prioritetskonti omfatter (men er ikke begrænset til) administrerende direktører, SNG'er, CFO'er, infrastrukturadministratorkonti, oprettelse af systemkonti med mere.

For hackere er almindelige phishingangreb, der kaster et tilfældigt net til almindelige eller ukendte brugere, ineffektive. På den anden side er _spyd phishing_ - eller _hvalfangstangreb_ , der er rettet mod prioriterede konti, meget givende for angribere. Derfor kræver prioritetskonti stærkere end almindelig beskyttelse for at forhindre, at kontoen kompromitteres.

Microsoft 365 og Microsoft Defender for Office 365 indeholder flere vigtige funktioner, der giver yderligere sikkerhedslag for dine prioritetskonti. I denne artikel beskrives disse funktioner, og hvordan du bruger dem.

:::image type="content" source="../../media/security-recommendations-for-priority-users.png" alt-text="Oversigten over sikkerhedsanbefalinger i ikonformat" lightbox="../../media/security-recommendations-for-priority-users.png":::

|Opgave|Alle Office 365 Enterprise planer|Microsoft 365 E3|Microsoft 365 E5|
|---|:---:|:---:|:---:|
|[Forøg logonsikkerhed for prioritetskonti](#increase-sign-in-security-for-priority-accounts)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Brug strenge forudindstillede sikkerhedspolitikker for prioritetskonti](#use-strict-preset-security-policies-for-priority-accounts)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Anvend brugerkoder på prioritetskonti](#apply-user-tags-to-priority-accounts)|||![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Overvåg prioritetskonti i beskeder, rapporter og registreringer](#monitor-priority-accounts-in-alerts-reports-and-detections)|||![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|
|[Oplær brugere](#train-users)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../../media/d238e041-6854-4a78-9141-049224df0795.png)|

> [!NOTE]
> Du kan finde oplysninger om sikring af _privilegerede konti_ (administratorkonti) i [dette emne](/security/compass/critical-impact-accounts).

## <a name="increase-sign-in-security-for-priority-accounts"></a>Forøg logonsikkerhed for prioritetskonti

Prioritetskonti kræver øget logonsikkerhed. Du kan øge deres logonsikkerhed ved at kræve multifaktorgodkendelse (MFA) og deaktivere ældre godkendelsesprotokoller.

Du kan finde instruktioner under [Trin 1. Øg logonsikkerheden for fjernarbejdere med MFA](../../solutions/empower-people-to-work-remotely-secure-sign-in.md). Selvom denne artikel handler om fjernarbejdere, gælder de samme begreber for prioriterede brugere.

**Bemærk**! Vi anbefaler på det kraftigste, at du globalt deaktiverer ældre godkendelsesprotokoller for alle prioriterede brugere, som beskrevet i forrige artikel. Hvis dine forretningskrav forhindrer dig i at gøre det, indeholder Exchange Online følgende kontrolelementer for at begrænse omfanget af ældre godkendelsesprotokoller:

- Du kan bruge [godkendelsespolitikker](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) og [regler for klientadgang](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules) i Exchange Online til at blokere eller tillade basisgodkendelse og ældre godkendelsesprotokoller, f.eks. POP3, IMAP4 og godkendt SMTP for bestemte brugere.

- Du kan deaktivere adgang til POP3 og IMAP4 i individuelle postkasser. Du kan deaktivere godkendt SMTP på organisationsniveau og aktivere det i bestemte postkasser, der stadig kræver det. Du kan finde instruktioner i følgende artikler:
  - [Aktivér eller deaktiver pop3- eller IMAP4-adgang for en bruger](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)
  - [Aktivér eller deaktiver godkendt afsendelse af KLIENT-SMTP (SMTP AUTH)](/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission)

Det er også værd at bemærke, at basisgodkendelse frarådes i Exchange Online for Exchange Web Services (EWS), Exchange ActiveSync, POP3, IMAP4 og ekstern PowerShell. Du kan finde flere oplysninger i dette [blogindlæg](https://developer.microsoft.com/office/blogs/deferred-end-of-support-date-for-basic-authentication-in-exchange-online/).

## <a name="use-strict-preset-security-policies-for-priority-accounts"></a>Brug strenge forudindstillede sikkerhedspolitikker for prioritetskonti

Prioriterede brugere kræver strengere handlinger for de forskellige beskyttelser, der er tilgængelige i Exchange Online Protection (EOP) og Defender for Office 365.

I stedet for f.eks. at levere meddelelser, der er klassificeret som spam, til mappen Uønsket mail, skal du sætte de samme meddelelser i karantæne, hvis de er beregnet til prioriterede konti.

Du kan implementere denne strenge tilgang for prioritetskonti ved hjælp af profilen Strict i forudindstillede sikkerhedspolitikker.

Forudindstillede sikkerhedspolitikker er en praktisk og central placering, hvor du kan anvende vores anbefalede Strenge politikindstillinger for al beskyttelse i EOP og Defender for Office 365. Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

Du kan finde oplysninger om, hvordan politikindstillingerne Strict adskiller sig fra standard- og Standard-politikindstillingerne, under [Anbefalede indstillinger for EOP og Microsoft Defender for Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

## <a name="apply-user-tags-to-priority-accounts"></a>Anvend brugerkoder på prioritetskonti

Brugertags i Microsoft Defender for Office 365 Plan 2 (som en del af Microsoft 365 E5 eller et tilføjelsesprogram) er en metode til hurtigt at identificere og klassificere bestemte brugere eller grupper af brugere i rapporter og efterforskninger af hændelser.

**Prioritetskonti** er en type indbygget brugerkode (kendt som et _systemmærke_), som du kan bruge til at identificere hændelser og beskeder, der omfatter prioritetskonti. Du kan få flere oplysninger om **prioritetskonti** under [Administrer og overvåg prioritetskonti](../../admin/setup/priority-accounts.md).

Du kan også oprette brugerdefinerede mærker for yderligere at identificere og klassificere dine prioritetskonti. Du kan få flere oplysninger under [Brugerkoder](user-tags.md). Du kan administrere **prioritetskonti** (systemkoder) i den samme grænseflade som brugerdefinerede brugerkoder.

## <a name="monitor-priority-accounts-in-alerts-reports-and-detections"></a>Overvåg prioritetskonti i beskeder, rapporter og registreringer

Når du har beskyttet og mærket dine prioriterede brugere, kan du bruge de tilgængelige rapporter, beskeder og undersøgelser i EOP og Defender for Office 365 til hurtigt at identificere hændelser eller registreringer, der involverer prioritetskonti. De funktioner, der understøtter brugerkoder, er beskrevet i følgende tabel.

|Funktion|Beskrivelse|
|---|---|
|Beskeder|De berørte brugeres brugerkoder er synlige og tilgængelige som filtre på siden **Beskeder** på portalen Microsoft 365 Defender. Du kan få flere oplysninger under [Visning af beskeder](../../compliance/alert-policies.md#viewing-alerts).|
|Explorer <p> Registreringer i realtid|I **Stifinder** (Defender for Office 365 Plan 2) eller **registreringer i realtid** (Defender for Office 365 Plan 1) er brugerkoder synlige i gittervisningen Mail og pop op-vinduet Mailoplysninger. Brugerkoder er også tilgængelige som en egenskab, der kan filtreres. Du kan få flere oplysninger  [under Mærker i Stifinder](threat-explorer.md#tags-in-threat-explorer).|
|Kampagnevisninger|Brugerkoder er en af mange egenskaber, der kan filtreres, i kampagnevisninger i Microsoft Defender for Office 365 Plan 2. Du kan få flere oplysninger under [Kampagnevisninger](campaigns.md).|
|Statusrapport om trusselsbeskyttelse|I stort set alle visnings- og detaljetabeller i **rapporten Over trusselsbeskyttelsesstatus** kan du filtrere resultaterne efter **prioriterede konti**. Du kan få flere oplysninger under [Rapport over status for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report).|
|Rapport over mailproblemer for prioritetskonti|Rapporten **Mailproblemer for prioritetskonti** i Exchange Administration (EAC) indeholder oplysninger om ikke-leverede og forsinkede meddelelser for **prioritetskonti**. Du kan få flere oplysninger i [Rapporten Mailproblemer for prioritetskonti](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report).|

## <a name="train-users"></a>Oplær brugere

Oplæring af brugere med prioritetskonti kan hjælpe med at spare disse brugere og dit sikkerhedsteam meget tid og frustration. Kyndige brugere er mindre tilbøjelige til at åbne vedhæftede filer eller klikke på links i tvivlsomme mails, og de er mere tilbøjelige til at undgå mistænkelige websteder.

Harvard Kennedy School [Cybersecurity Campaign Handbook](https://www.belfercenter.org/CyberPlaybook) giver fremragende vejledning til at etablere en stærk kultur af sikkerhedsbevidsthed i din organisation, herunder træning af brugere til at identificere phishing-angreb.

Microsoft 365 indeholder følgende ressourcer, der kan hjælpe med at informere brugerne i din organisation:

|Koncept|Ressourcer|Beskrivelse|
|---|---|---|
|Microsoft 365|[Læringsforløb, der kan tilpasses](/office365/customlearning/)|Disse ressourcer kan hjælpe dig med at sammensætte kurser for brugere i din organisation.|
|Microsoft 365-sikkerhed|[Learning modul: Beskyt din organisation med indbygget intelligent sikkerhed fra Microsoft 365](/learn/modules/security-with-microsoft-365)|I dette modul kan du beskrive, hvordan Microsoft 365 sikkerhedsfunktioner arbejder sammen og formulere fordelene ved disse sikkerhedsfunktioner.|
|Multifaktorgodkendelse|[Totrinsbekræftelse: Hvad er den ekstra bekræftelsesside?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)|Denne artikel hjælper slutbrugerne med at forstå, hvad multifaktorgodkendelse er, og hvorfor den bruges i din organisation.|
|Oplæring i angrebssimulering|[Kom i gang med at bruge kursus i angrebssimulering](attack-simulation-training-get-started.md)|Oplæring i simulering af angreb i Microsoft Defender for Office 365 Plan 2 gør det muligt for administratoren at konfigurere, starte og spore simulerede phishing-angreb mod bestemte grupper af brugere.|

Derudover anbefaler Microsoft, at brugerne foretager de handlinger, der er beskrevet i denne artikel: [Beskyt din konto og dine enheder mod hackere og malware](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Disse handlinger omfatter:

- Brug af stærke adgangskoder
- Beskyttelse af enheder
- Aktivering af sikkerhedsfunktioner på Windows- og Mac-pc'er (til ikke-administrerede enheder)

## <a name="see-also"></a>Se også

[Meddelelse om prioritetskontobeskyttelse i Microsoft Defender for Office 365](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/announcing-priority-account-protection-in-microsoft-defender-for/ba-p/1696385)
