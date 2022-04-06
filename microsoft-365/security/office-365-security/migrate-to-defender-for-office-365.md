---
title: Overfør fra en tredjepartsbeskyttelsestjeneste til Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Lær den rigtige måde at overføre fra tredjeparts beskyttelsestjenester eller enheder som Google Postini, Barracuda Spam og Virus Firewall eller Cisco IronPort til Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: af24829f8d3e4186de6e1c537d545515667627b8
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682345"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Overfør fra en tredjepartsbeskyttelsestjeneste eller -enhed til Microsoft Defender for Office 365

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)

Hvis du allerede har en eksisterende tredjepartsbeskyttelsestjeneste eller -enhed, der står foran Microsoft 365, kan du bruge denne vejledning til at overføre beskyttelsen til Microsoft Defender til Office 365 for at få fordelene ved en konsolideret administrationsoplevelse, potentielt reducerede omkostninger (ved hjælp af produkter, du allerede betaler for), og et modent produkt med integreret sikkerhedsbeskyttelse. Du kan finde flere oplysninger [i Microsoft Defender for Office](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Denne vejledning indeholder specifikke og handlingserbare trin til din overførsel og antager følgende fakta:

- Du har allerede Microsoft 365 postkasser, men du bruger i øjeblikket en tredjepartstjeneste eller -enhed til mailbeskyttelse. Mail fra internettet flyder gennem beskyttelsestjenesten før levering til din Microsoft 365-organisation, og Microsoft 365-beskyttelse er så lav som muligt (den er aldrig helt slået fra; f.eks. gennemtvinges malwarebeskyttelse altid).

  ![Mail flyder fra internettet via tredjepartsbeskyttelsestjenesten eller -enheden, før de leveres Microsoft 365.](../../media/mdo-migration-before.png)

- Du er uden for undersøgelsen og overvejelsesfasen for beskyttelse af Defender Office 365. Hvis du har brug for at evaluere Defender Office 365 at beslutte, om det er det rigtige for din organisation, anbefaler vi, at du overvejer [Evalueringstilstand](office-365-evaluation.md).

- Du har allerede købt Defender til Office 365 licenser.

- Du skal lade din eksisterende tredjepartsbeskyttelsestjeneste udgå, hvilket betyder, at du i sidste ende skal pege MX-posterne for dine maildomæner tilbage Microsoft 365. Når du er færdig, sendes mails fra internettet direkte til Microsoft 365 og vil være beskyttet udelukkende af Exchange Online Protection (EOP) og Defender Office 365.

  ![Din eksisterende beskyttelsestjeneste eller enheder er slettet, så mails flyder fra internettet til Microsoft 365 med fuld beskyttelse fra Microsoft Defender Office 365.](../../media/mdo-migration-after.png)

At eliminere din eksisterende beskyttelsestjeneste i stedet for Defender for Office 365 er et stort skridt, som du ikke bør tage let, og du skal heller ikke skynde dig at foretage ændringen. Vejledningen i denne overførselsvejledning kan hjælpe dig med at overgå din beskyttelse på en velordent måde med minimal afbrydelse for dine brugere.

Overførselstrinnene på meget højt niveau er vist i følgende diagram. De faktiske trin er angivet i afsnittet [Overførselsprocessen senere](#the-migration-process) i denne artikel.

![Overfør fra en tredjepartsbeskyttelsesløsning eller -enhed til Defender for Office 365.](../../media/mdo-migration-overview.png)

## <a name="why-use-the-steps-in-this-guide"></a>Hvorfor bruge trinnene i denne vejledning?

I it-branchen er overraskelser generelt dårlige. Hvis du blot spejlvender dine MX-poster for at pege Microsoft 365 uden forudgående og gennemtænkte test, vil det resultere i mange overraskelser. Eksempel:

- Du eller dine foregående opgaver har sandsynligvis brugt en masse tid og energi på at tilpasse din eksisterende beskyttelsestjeneste til optimal levering af mail (med andre ord blokering af, hvad der skal blokeres, og at tillade, hvad der skal tillades). Det er næsten helt sikkert, at ikke alle tilpasninger i din aktuelle beskyttelsestjeneste er påkrævet i Defender Office 365. Det er også meget muligt, at Defender for Office 365 introducerer nye problemer (tillader eller blokke), som ikke skete eller ikke var påkrævet i din aktuelle beskyttelsestjeneste.
- Din helpdesk og sikkerhedsmedarbejder skal vide, hvad de skal gøre i Defender Office 365. Hvis en bruger f.eks. brokker sig over en manglende meddelelse, ved din helpdesk så, hvor eller hvordan du skal lede efter den? De ved sandsynligvis godt om værktøjerne i din eksisterende beskyttelsestjeneste, men hvad med værktøjerne i Defender til Office 365?

Hvis du derimod følger trinnene i denne overførselsvejledning, får du følgende fordele til din overførsel:

- Minimal afbrydelse for brugere.
- Måldata fra Defender for Office 365, som du kan bruge, når du rapporterer om status og succes med overførslen til ledelsen.
- Tidlig deltagelse og instruktion for helpdesk- og sikkerhedsmedarbejdere.

Jo mere du bliver fortrolig med, hvordan Defender for Office 365 påvirker din organisation, jo bedre bliver overgangen for brugere, helpdeskmedarbejdere, sikkerhedsmedarbejdere og administration.

Denne overførselsvejledning giver dig en plan for gradvist at "dreje skiven", så du kan overvåge og teste, hvordan Defender til Office 365 påvirker dine brugere og deres mail, så du kan reagere hurtigt på eventuelle problemer, du støder på.

## <a name="the-migration-process"></a>Overførselsprocessen

Processen med at overføre fra en tredjepartsbeskyttelsestjeneste til Defender for Office 365 kan opdeles i tre faser som beskrevet i følgende tabel:

![Processen for overførsel til Defender for Office 365.](../../media/phase-diagrams/migration-phases.png)

|Fase|Beskrivelse|
|---|---|
|[Forberede din overførsel](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Opliste indstillingerne på din eksisterende beskyttelsestjeneste](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Kontrollér din eksisterende beskyttelseskonfiguration i Microsoft 365](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Kontrollér din mailroutingkonfiguration](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[Flyt funktioner, der redigerer meddelelser, Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[Definere spam og massebrugeroplevelser](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Identificer og angiv prioritetskonti](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Konfigurer Defender til Office 365](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Opret distributionsgrupper for pilotbrugere](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Konfigurere brugerindsendelse til rapportering af brugermeddelelse](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[Vedligeholde eller oprette reglen for mailflow i SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Konfigurere udvidet filtrering for forbindelser](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Opret pilotbeskyttelsespolitikker](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Onboard to Defender for Office 365](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Begynd onboardingsikkerhedsopdateringer Teams](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(Valgfrit) Undtage pilotbrugere fra filtrering af din eksisterende beskyttelsestjeneste](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Finjuster efterlignet intelligens](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Finjustere repræsentationsbeskyttelse og postkasseintelligens](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Brug data fra brugerindsendelser til at måle og justere](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(Valgfrit) Føj flere brugere til dit pilotprojekt og din testning](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[Udvide Microsoft 365 beskyttelse af mail til alle brugere og deaktivere reglen for mailflow i SCL=-1](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[Skifte dine MX-poster](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>Næste trin

- Fortsæt til [Fase 1: Forbered](migrate-to-defender-for-office-365-prepare.md).
