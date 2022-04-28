---
title: Overfør fra en beskyttelsestjeneste fra tredjepart til Microsoft Defender for Office 365
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
description: Få mere at vide om den rigtige måde at migrere fra beskyttelsestjenester eller enheder fra tredjepart, f.eks. Google Postini, Barracuda Spam og Virus Firewall, eller Cisco IronPort for at Microsoft Defender for Office 365 beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2f67135e2b8a3700a2fb6a6e24fc4f66696db2e3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098708"
---
# <a name="migrate-from-a-third-party-protection-service-or-device-to-microsoft-defender-for-office-365"></a>Overfør fra en beskyttelsestjeneste eller enhed fra tredjepart til Microsoft Defender for Office 365

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)

Hvis du allerede har en eksisterende beskyttelsestjeneste eller enhed fra tredjepart, der er placeret foran Microsoft 365, kan du bruge denne vejledning til at migrere din beskyttelse til Microsoft Defender for Office 365 for at få fordelene ved en konsolideret ledelsesoplevelse, potentielt reducerede omkostninger (ved hjælp af produkter, du allerede betaler for) og et modent produkt med integreret sikkerhed  Beskyttelse. Du kan få flere oplysninger under [Microsoft Defender for Office 365](https://www.microsoft.com/security/business/threat-protection/office-365-defender).

Denne vejledning indeholder specifikke trin, der kan handles på, for din migrering og antager følgende fakta:

- Du har allerede Microsoft 365 postkasser, men du bruger i øjeblikket en tredjepartstjeneste eller -enhed til mailbeskyttelse. Mails fra internettet flyder gennem beskyttelsestjeneste, før de leveres til din Microsoft 365 organisation, og Microsoft 365 beskyttelse er så lav som muligt (det er aldrig helt slukket, for eksempel gennemtvinges malwarebeskyttelse altid).

  :::image type="content" source="../../media/mdo-migration-before.png" alt-text="Mailen flyder fra internettet via beskyttelsestjeneste fra tredjepart eller enhed, før den leveres til Microsoft 365" lightbox="../../media/mdo-migration-before.png":::

- Du er uden for undersøgelses- og overvejelsesfasen for beskyttelse af Defender for Office 365. Hvis du har brug for at evaluere Defender for Office 365 for at beslutte, om det er korrekt for din organisation, anbefaler vi, at du overvejer de indstillinger, der er beskrevet i [Prøv Microsoft Defender for Office 365](try-microsoft-defender-for-office-365.md).

- Du har allerede købt Defender for Office 365 licenser.

- Du skal trække din eksisterende beskyttelsestjeneste fra tredjepart tilbage, hvilket betyder, at du i sidste ende skal pege MX-posterne for dine maildomæner for at Microsoft 365. Når du er færdig, overføres mails fra internettet direkte til Microsoft 365 og beskyttes udelukkende af Exchange Online Protection (EOP) og Defender for Office 365.

  :::image type="content" source="../../media/mdo-migration-after.png" alt-text="Mailen flyder fra internettet til Microsoft 365" lightbox="../../media/mdo-migration-after.png":::

Eliminering af din eksisterende beskyttelsestjeneste til fordel for Defender for Office 365 er et stort skridt, som du ikke bør tage let på, og du skal heller ikke skynde dig at foretage ændringen. Vejledningen i denne migreringsvejledning hjælper dig med at skifte din beskyttelse på en ordnet måde med minimal afbrydelse for dine brugere.

Overførselstrinnene på meget højt niveau er illustreret i følgende diagram. De faktiske trin er angivet i afsnittet [Migreringsprocessen](#the-migration-process) senere i denne artikel.

:::image type="content" source="../../media/mdo-migration-overview.png" alt-text="Processen med overførsel fra en tredjepartsbeskyttelsesløsning eller -enhed til Defender for Office 365" lightbox="../../media/mdo-migration-overview.png":::

## <a name="why-use-the-steps-in-this-guide"></a>Hvorfor bruge trinnene i denne vejledning?

I it-branchen er overraskelser generelt dårlige. Blot spejlvende dine MX-poster for at pege på Microsoft 365 uden forudgående og betænksom test vil resultere i mange overraskelser. Eksempel:

- Du eller dine forgængere har sandsynligvis brugt en masse tid og kræfter på at tilpasse din eksisterende beskyttelsestjeneste til optimal levering af post (med andre ord blokere for, hvad der skal blokeres, og tillade, hvad der skal tillades). Det er næsten en garanteret sikkerhed, at det ikke er alle tilpasninger i din aktuelle beskyttelsestjeneste, der kræves i Defender for Office 365. Det er også meget muligt, at Defender for Office 365 vil introducere nye problemer (tillader eller blokerer), der ikke skete eller ikke var påkrævet i din aktuelle beskyttelsestjeneste.
- Din helpdesk og sikkerhedsafdelingen skal vide, hvad de skal gøre i Defender for Office 365. Hvis en bruger f.eks. klager over en manglende meddelelse, ved din helpdesk så, hvor eller hvordan man leder efter den? De kender sikkert værktøjerne i din eksisterende beskyttelsestjeneste, men hvad med værktøjerne i Defender for Office 365?

Hvis du derimod følger trinnene i denne migreringsvejledning, får du følgende konkrete fordele for din migrering:

- Minimal afbrydelse for brugerne.
- Objektive data fra Defender for Office 365, som du kan bruge, når du rapporterer om fremskridtet og succesen af migreringen til administration.
- Tidlig involvering og instruktion til helpdesk og sikkerhedspersonale.

Jo mere du bliver fortrolig med, hvordan Defender for Office 365 påvirker din organisation, jo bedre bliver overgangen for brugere, helpdeskpersonale, sikkerhedspersonale og administration.

Denne migreringsvejledning giver dig en plan for gradvis at "dreje opkaldet", så du kan overvåge og teste, hvordan Defender for Office 365 påvirker dine brugere og deres e-mail, så du hurtigt kan reagere på eventuelle problemer, du støder på.

## <a name="the-migration-process"></a>Migreringsprocessen

Processen med at migrere fra en tredjepartsbeskyttelsestjeneste til Defender for Office 365 kan opdeles i tre faser, som beskrevet i følgende tabel:

:::image type="content" source="../../media/phase-diagrams/migration-phases.png" alt-text="Processen for overførsel til Defender for Office 365" lightbox="../../media/phase-diagrams/migration-phases.png":::

|Fase|Beskrivelse|
|---|---|
|[Forbered migreringen](migrate-to-defender-for-office-365-prepare.md)|<ol><li>[Oversigt over indstillingerne på din eksisterende beskyttelsestjeneste](migrate-to-defender-for-office-365-prepare.md#inventory-the-settings-at-your-existing-protection-service)</li><li>[Kontrollér din eksisterende beskyttelseskonfiguration i Microsoft 365](migrate-to-defender-for-office-365-prepare.md#check-your-existing-protection-configuration-in-microsoft-365)</li><li>[Kontrollér konfigurationen af postdistributionen](migrate-to-defender-for-office-365-prepare.md#check-your-mail-routing-configuration)</li><li>[Flyt funktioner, der ændrer meddelelser, til Microsoft 365](migrate-to-defender-for-office-365-prepare.md#move-features-that-modify-messages-into-microsoft-365)</li><li>[Definer spam og massebrugeroplevelser](migrate-to-defender-for-office-365-prepare.md#define-spam-and-bulk-user-experiences)</li><li>[Identificer og angiv prioritetskonti](migrate-to-defender-for-office-365-prepare.md#identify-and-designate-priority-accounts)</li></ol>|
|[Konfigurer Defender for Office 365](migrate-to-defender-for-office-365-setup.md)|<ol><li>[Opret distributionsgrupper til pilotbrugere](migrate-to-defender-for-office-365-setup.md#step-1-create-distribution-groups-for-pilot-users)</li><li>[Konfigurer brugerindsendelse til rapportering af brugermeddelelser](migrate-to-defender-for-office-365-setup.md#step-2-configure-user-submission-for-user-message-reporting)</li><li>[Vedligehold eller opret reglen for SCL=-1-mailflow](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule)</li><li>[Konfigurer udvidet filtrering for forbindelser](migrate-to-defender-for-office-365-setup.md#step-4-configure-enhanced-filtering-for-connectors)</li><li>[Opret pilotbeskyttelsespolitikker](migrate-to-defender-for-office-365-setup.md#step-5-create-pilot-protection-policies)</li></ol>|
|[Onboard til Defender for Office 365](migrate-to-defender-for-office-365-onboard.md)|<ol><li>[Begynd onboarding af Teams for sikkerhed](migrate-to-defender-for-office-365-onboard.md#step-1-begin-onboarding-security-teams)</li><li>[(Valgfrit) Undtaget pilotbrugere fra filtrering efter din eksisterende beskyttelsestjeneste](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)</li><li>[Juster spoof intelligence](migrate-to-defender-for-office-365-onboard.md#step-3-tune-spoof-intelligence)</li><li>[Juster repræsentationsbeskyttelse og postkasseintelligens](migrate-to-defender-for-office-365-onboard.md#step-4-tune-impersonation-protection-and-mailbox-intelligence)</li><li>[Brug data fra brugerindsendelser til at måle og justere](migrate-to-defender-for-office-365-onboard.md#step-5-use-data-from-user-submissions-to-measure-and-adjust)</li><li>[(Valgfrit) Føj flere brugere til din pilot, og gentage](migrate-to-defender-for-office-365-onboard.md#step-6-optional-add-more-users-to-your-pilot-and-iterate)</li><li>[Udvid Microsoft 365 beskyttelse til alle brugere, og slå reglen for SCL=-1-mailflow fra](migrate-to-defender-for-office-365-onboard.md#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)</li><li>[Skift dine MX-poster](migrate-to-defender-for-office-365-onboard.md#step-8-switch-your-mx-records)</li></ol>|

## <a name="next-step"></a>Næste trin

- Fortsæt til [fase 1: Forbered](migrate-to-defender-for-office-365-prepare.md).
